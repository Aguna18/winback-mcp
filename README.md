# Winback MCP server

Winback (Winback HQ) wins back cancelled, billing-failed and expired-trial subscribers for RevenueCat and Stripe apps with one personal message each, offers only inside limits the founder sets, and charges only when someone comes back.

This MCP server answers product, pricing and fit questions about Winback, estimates win-back revenue the same way the website calculator does, and returns sourced Apple retention facts. It reads no customer data.

- **Endpoint:** `https://winbackhq.com/mcp/`
- **Transport:** Streamable HTTP
- **Sign-in:** none. No API key, no account.
- **Access:** every tool is read-only.
- **MCP Registry name:** `io.github.Aguna18/winback`

This repository holds setup instructions and the registry entry only. It contains no product code.

## Add it to Claude

Customize, Connectors, Add, Add custom connector, then paste:

```
https://winbackhq.com/mcp/
```

ChatGPT: in developer mode, add a connector with the same URL.

## Cursor, VS Code, Windsurf and other clients

Add this to your MCP config:

```json
{
  "mcpServers": {
    "winback": {
      "type": "http",
      "url": "https://winbackhq.com/mcp/"
    }
  }
}
```

## Tools

| Tool | What it returns |
| --- | --- |
| `get_winback_overview` | What Winback does, who it is for, the three segments it works on and what it never does. |
| `get_winback_pricing` | No monthly fee, 15% of revenue from returners for 6 months. |
| `estimate_win_back_revenue` | The same estimate as the revenue calculator: subscribers won back, revenue, fee and what you keep. |
| `get_apple_retention_facts` | Sourced facts on billing retry, grace periods, win-back offers and Retention Messaging. |

A GET request to `https://winbackhq.com/mcp/` shows the server's name and tools.

## Things to ask it

- How do I win back churned subscribers of my RevenueCat app without a monthly fee?
- We lose 300 subscribers a month at $40 a year. What could a win-back bring in?
- How long does Apple retry a failed subscription payment?

## Privacy

The server reads no customer data and stores nothing you send it. It only answers questions about Winback and runs estimates from the numbers you give it. Full policy: https://winbackhq.com/privacy/

## Links

- Website: https://winbackhq.com/
- Guide for AI agents: https://winbackhq.com/agents/
- Privacy: https://winbackhq.com/privacy/

## Registry publishing

`server.json` is published to the official MCP Registry (registry.modelcontextprotocol.io) by `.github/workflows/publish-mcp.yml`, which logs in with GitHub OIDC. No token is stored in this repository.

---

Made by AGUNA WELLNESS LTD.

The MIT license covers the files in this repository.
