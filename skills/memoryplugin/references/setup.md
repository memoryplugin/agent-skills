# Connecting MemoryPlugin

MemoryPlugin is a remote MCP server. Authentication is OAuth in the browser (with PKCE and dynamic client registration), so there are no API keys to paste. The user needs a MemoryPlugin account: https://www.memoryplugin.com

Endpoints:

- HTTP (preferred): `https://www.memoryplugin.com/api/mcp/mcp`
- SSE (fallback): `https://www.memoryplugin.com/api/mcp/sse`

Full docs: https://help.memoryplugin.com/integrations/remote-mcp-server

## Claude Code

```bash
claude mcp add --transport http memoryplugin https://www.memoryplugin.com/api/mcp/mcp
```

Then run `/mcp` inside Claude Code to complete the browser sign-in. Installing the MemoryPlugin plugin (`/plugin marketplace add memoryplugin/agent-skills`, then `/plugin install memoryplugin@memoryplugin`) configures the server automatically.

## Claude (web and desktop)

Settings, then Connectors, then "Add custom connector". Paste `https://www.memoryplugin.com/api/mcp/mcp` and approve the browser sign-in.

## ChatGPT

Settings, then Apps, then Advanced, then enable Developer mode. Add a custom connector with the HTTP endpoint above and OAuth. Note: on Plus and Pro plans ChatGPT currently allows read-only tools from custom connectors, so recall works but storing may require a Business plan or the MemoryPlugin browser extension.

## Codex CLI

```bash
codex mcp add memoryplugin --url https://www.memoryplugin.com/api/mcp/mcp
codex mcp login memoryplugin
```

## Cursor, Windsurf, VS Code, other MCP clients

Add a server of type `http` with the endpoint above. Example `mcp.json` entry:

```json
{
  "mcpServers": {
    "memoryplugin": {
      "type": "http",
      "url": "https://www.memoryplugin.com/api/mcp/mcp"
    }
  }
}
```

For clients without remote MCP support, use the `mcp-remote` proxy:

```json
{
  "mcpServers": {
    "memoryplugin": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://www.memoryplugin.com/api/mcp/mcp"]
    }
  }
}
```

## Browser extension

For ChatGPT, Claude, Gemini, and 20+ other AI web apps, the MemoryPlugin browser extension adds memory directly in the page, no MCP needed: https://www.memoryplugin.com
