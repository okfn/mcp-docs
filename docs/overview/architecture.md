# Architecture

Three moving parts, one contract between them.

The **gateway is the only initiator**: it calls both the LLM and the MCP
server and waits for each reply. The LLM and the MCP server never talk to
each other, and the MCP server cannot interrupt: it only ever speaks when
spoken to.

That is about *timing*. It is not about *content*. When the gateway calls
a tool, it asks only for that tool to run, but the tool decides what
comes back, and anything it puts in `structuredContent` is rendered
straight to the screen. A tool can return a table, a chart, or a `force`
message, and the interface will display it without the AI or the gateway
approving it first. **Tool code has direct write access to the chat.**
That is deliberate: it is what makes the numbers on screen come from
human-written code instead of from the model.

```mermaid
sequenceDiagram
    actor User
    participant Gateway as Chat gateway
    participant LLM
    participant MCP as MCP server
    participant Tool as Plugin tool
    participant Data as Datasets

    User->>Gateway: question
    Gateway->>LLM: question + tool catalog
    LLM-->>Gateway: call this tool, with these arguments
    Gateway->>MCP: run that tool
    MCP->>Tool: dispatch to the plugin's function
    Tool->>Data: read
    Data-->>Tool: rows
    Tool-->>MCP: text + tables/charts/sources
    MCP-->>Gateway: that result, unchanged
    Gateway->>LLM: the tool's text only
    LLM-->>Gateway: the answer, in words
    Gateway-->>User: those words, plus tables/charts drawn from the data
```

That is the whole runtime picture, and time runs downward. The LLM
answers the gateway **twice, at two different moments**, and the two
replies are not the same kind of thing:

- **The first reply names a tool.** The model has not seen any data yet.
  It is looking at the tool catalog and picking one, so this reply is a
  request, not an answer.
- **The last reply is the answer.** By now the tool has run and the
  gateway has handed the model the tool's text, so the model is writing
  prose about data it has actually been given.

The middle of the diagram can repeat: if the model wants a second tool,
it asks again and the cycle runs once more before the final reply.

The last two arrows are worth reading together. Only the tool's **text**
goes back to the LLM; the tables and charts skip the model entirely and
travel from the tool to the user's screen. That is the same point made
above, drawn as a path.

## Where the plugin sits

The **plugin tool** is the only part of this picture that knows anything
about a specific dataset. Everything above it is generic: the gateway,
the LLM and the MCP server would work identically over parliamentary
amendments or over an energy balance. Everything below it is a file.

The MCP server does not read data. It receives a call, dispatches to the
plugin function registered under that name, and passes the result back
out **unchanged**. So the numbers a user sees were computed by code from
a country's plugin repo, by people who know that data, which is exactly
why plugins are [scoped to a domain someone
understands](../lessons/scope.md).

## The flow of a question

1. The user types a question in the **chat gateway**.
2. The gateway asks the **MCP server** for its tool catalog (`tools/list`).
   This happens on the gateway's own initiative, before the AI is
   involved.
3. The gateway sends the conversation plus that tool catalog to the LLM.
4. The LLM does not call anything itself. It replies with the **name** of
   a tool and the parameters to use, or with a final text answer.
5. If a tool was named, the gateway calls it on the MCP server
   (`tools/call`). The server runs the tool against the real dataset and
   **returns** two things in its reply: a text answer for the LLM, and a
   structured payload (sources, tables, charts) for the UI.
6. The gateway feeds the text back to the LLM (which may then answer or
   call another tool), and renders the structured parts itself: source
   links, tables, Chart.js charts.

So the MCP server never opens a connection to the chat on its own. But
within the reply to a call the gateway made, the tool decides what the
user sees, and the gateway renders it as-is. A tool can even return a
`force` message: text shown directly to the user as its own message,
which is never added to the conversation the LLM reads. In that case the
tool is talking to the human over the model's head, by design.

## The contract

Every tool returns both a human-readable text (for the LLM) and a
`structuredContent` payload (for the UI) that must include the data
sources. Crucially, only the text is sent to the model; the tables and
charts in `structuredContent` are rendered straight to the interface,
**never passing through the AI**. They are produced by human-written
tool code, so they show exactly what was computed from the data. This
contract is what keeps answers traceable, and it is described in detail
in [tool results](../plugins/tool-results.md).

## Transports

The MCP server speaks two transports:

- **stdio**: for local use, e.g. plugging it into Claude Desktop.
- **HTTP**: for real deployments, where the gateway (or any client)
  connects over the network.
