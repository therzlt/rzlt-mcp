# RZLT connector for AI assistants (MCP)

[![Listed on mcpservers.org](https://mcpservers.org/badge.svg)](https://mcpservers.org/servers/therzlt/rzlt-mcp) [![RZLT MCP connector](https://glama.ai/mcp/connectors/io.rzlt/connector/badges/score.svg)](https://glama.ai/mcp/connectors/io.rzlt/connector)

Ask RZLT from your AI assistant. RZLT ([rzlt.io](https://www.rzlt.io)) is an AI-native growth and marketing agency for technology companies, B2B and B2C, and a Google Partner. This remote [Model Context Protocol](https://modelcontextprotocol.io) server lets Claude, ChatGPT, Cursor, VS Code and other MCP clients answer questions about RZLT from the source: what it does, its case studies, its writing, whether a company is a fit, and how to book a call.

```
https://mcp.rzlt.io/mcp
```

- Transport: Streamable HTTP
- Authentication: none
- Read-only: every tool only reads public information (from rzlt.io, or the public website you ask it to check)
- Cost: free

## Tools

| Tool | What it does |
|---|---|
| `rzlt_overview` | What RZLT is and sells: the four core services, how the work is delivered, credentials, pricing (from €5,000 a month) and how the first weeks run. |
| `find_case_studies` | RZLT's results for an industry or need, e.g. `"B2B SaaS"`, `"fintech"`, `"AI"`; `"launch"`, `"pipeline"`, `"SEO"`. |
| `search_rzlt` | Search everything on rzlt.io: services, industries, case studies and 300+ blog posts on growth, paid ads, SEO, AEO and AI marketing. |
| `check_fit` | A quick, rule-based check of whether a company fits RZLT's ideal client (technology companies, seed to Series C, €1M+ in revenue or funding). |
| `check_ai_readiness` | Free: checks whether a website is ready for AI assistants and search (AI crawlers allowed, llms.txt, structured data, text without JavaScript, title, sitemap…), with a score out of 100 and the 3 most important fixes. Reads only public pages and stores nothing. |
| `book_call` | The link to book a free 30-minute call, and what happens on it. It doesn't book anything itself. |

## Add it

**Claude** (claude.ai, Desktop, mobile): Settings → Connectors → Add custom connector → name `RZLT`, URL `https://mcp.rzlt.io/mcp`.

**Claude Code**

```bash
claude mcp add --transport http rzlt https://mcp.rzlt.io/mcp
```

**ChatGPT**: Settings → Apps & Connectors → Create (developer mode) → URL `https://mcp.rzlt.io/mcp`, no authentication.

**Cursor**: [Add to Cursor](https://cursor.com/en/install-mcp?name=rzlt&config=eyJ1cmwiOiJodHRwczovL21jcC5yemx0LmlvL21jcCJ9), or in `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "rzlt": { "url": "https://mcp.rzlt.io/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`):

```json
{ "servers": { "rzlt": { "type": "http", "url": "https://mcp.rzlt.io/mcp" } } }
```

**Any other client**: point it at `https://mcp.rzlt.io/mcp` (Streamable HTTP). For stdio-only clients:

```bash
npx -y mcp-remote https://mcp.rzlt.io/mcp
```

## Try asking

- "What does RZLT do, and what does it cost?"
- "Show me RZLT's case studies in fintech."
- "Has RZLT written about answer engine optimization?"
- "Is example.com ready for AI assistants?"
- "We're a Series A B2B SaaS company with €3M raised. Are we a fit for RZLT?"

## Privacy

The connector is public and read-only. It keeps no account data. For abuse protection and to improve answers it counts calls per tool and per client, and keeps the text of search questions for up to 90 days, without IP addresses. See [rzlt.io/privacy](https://www.rzlt.io/privacy).

## Contact

[Book a call](https://www.rzlt.io/book-a-call) · hello@rzlt.io

This repository holds the connector's public listing (`server.json`) for the [MCP Registry](https://registry.modelcontextprotocol.io). The server itself runs at mcp.rzlt.io.
