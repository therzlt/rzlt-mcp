# Installing the RZLT connector

The RZLT connector is a remote MCP server. Nothing needs to be downloaded, built or configured, and it needs no API key.

- URL: `https://mcp.rzlt.io/mcp`
- Transport: Streamable HTTP
- Authentication: none

Add it to the MCP settings like this:

```json
{
  "mcpServers": {
    "rzlt": {
      "type": "streamableHttp",
      "url": "https://mcp.rzlt.io/mcp"
    }
  }
}
```

If the client only supports stdio, use the `mcp-remote` bridge instead:

```json
{
  "mcpServers": {
    "rzlt": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.rzlt.io/mcp"]
    }
  }
}
```

To check it works, call the `rzlt_overview` tool. It takes no arguments and returns what RZLT does.
