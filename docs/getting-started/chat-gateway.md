# Run the chat gateway

The gateway is the human face of the platform: a web chat where the AI
is steered to answer from MCP tool data rather than its own memory.

You need the [MCP server running](mcp-server.md) in HTTP mode first.

```bash
git clone https://github.com/okfn/mcp-chat-gateway
cd mcp-chat-gateway
uv sync
source .venv/bin/activate
```

Configure the AI provider, either by editing `local_settings.py` or
with environment variables:

| Variable | Example | Meaning |
|----------|---------|---------|
| `AI_API_KEY` | `sk-...` | Key for your LLM provider |
| `AI_BASE_URL` | `https://api.deepseek.com` | Any OpenAI-compatible endpoint |
| `AI_MODEL` | `deepseek-chat` | Model name |
| `MCP_URL` | `http://127.0.0.1:8063` | Where the MCP server lives |

Then run it:

```bash
python app.py            # serves on http://127.0.0.1:8064
flask run --debug        # alternative: debug mode on port 5000
```

Open `http://127.0.0.1:8064`, pick a suggested question or type your
own, and watch the answer arrive with its tables, charts and source
links.

!!! note "Disposable by design"
    The gateway is intentionally simple: plain HTML/JS/CSS, a minimal
    Flask backend, no frontend framework. It exists to test and
    demonstrate the platform; expect it to change quickly.
