# Architectural constraints

Two deliberate design choices shape the platform. Both are trade-offs,
made consciously, and both drew real user feedback during the pilots.

## Stateless gateway: no accounts, no database

**Design choice.** The system operates without user accounts, session
registration or a central database. Users can download individual
outputs (tables, charts or text blocks), but whole conversations are
not saved or shared server-side.

**Trade-off.** This eliminates database administration, data retention
compliance and user management overhead, keeping the server lightweight
and easy to deploy: there is no database to run, back up or secure, and
no personal data to look after.

The cost is real too. Missing chat history was the most repeated
product complaint in the pilot feedback: testers compare the chat with
the tools they use every day, and against that reference the missing
history and sharing are felt immediately.

Two things to keep in mind when weighing that complaint. Being a full
chat product was never in scope. And the chat gateway is only one
client: the MCP server follows the standard protocol, so it can be
plugged into existing third-party chat clients that already handle
account management, history and sharing. If a future deployment needs
those features in this gateway, that is the point at which adding
storage would be worth its extra weight.

## Structured presentation: tables and charts

**Design choice.** Tools return structured data (tables and charts)
alongside text responses to ensure answers are auditable and
verifiable. Users value this a lot; it is what makes an answer
checkable against the source.

**UI mitigation.** The flip side, reported by several pilot testers, is
that tables and charts were sometimes repeated or too verbose.
Structured outputs are therefore rendered minimised by default in the
interface: the full source records stay one click away without
flooding the conversation flow.

A better future fix is to detect when the same table or chart is being
drawn a second time and simply not repeat it. That deduplication is not
built yet; for now, minimising by default is the mitigation.
