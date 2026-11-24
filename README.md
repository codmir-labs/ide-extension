# Codmir IDE extension

This repository is the future home of the IDE extension for [Codmir](https://codmir.com).

## Status

There is no code here yet. The repository holds this page and the [license](LICENSE). Until there is an extension, your
editor's AI agent can work with Codmir over the [Model Context Protocol](https://modelcontextprotocol.io) (MCP).

## Use Codmir from your IDE today

There are two public servers. Pick one.

**The local server, [`@codmir/mcp`](https://github.com/codmir-labs/mcp).** It runs on your machine and needs Node.js 18
or later. To use your projects, sign in with the Codmir CLI. It runs on Bun, and its install adds Bun when needed.

```bash
npm install -g codmir
codmir login
```

| Editor | Where the server goes |
| ------ | --------------------- |
| VS Code with Copilot | The entry below, in `.mcp.json` at the root of the workspace ([docs](https://code.visualstudio.com/docs/agents/reference/mcp-configuration)) |
| Cursor | The entry below, in `.cursor/mcp.json` in the project ([docs](https://cursor.com/docs/mcp)) |
| Claude Code in [VS Code](https://code.claude.com/docs/en/vs-code) or [JetBrains](https://code.claude.com/docs/en/jetbrains) | In the terminal, `claude mcp add codmir -- npx -y -p @codmir/mcp codmir-mcp` |

```json
{
  "mcpServers": {
    "codmir": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "-p", "@codmir/mcp", "codmir-mcp"]
    }
  }
}
```

**The hosted connector.** It runs at Codmir and signs you in with OAuth in your browser. In Claude Code, add it, then
run `/mcp` in a session and sign in. The [plugin](https://github.com/codmir-labs/mcp-plugin-anthropic) adds it too.

```bash
claude mcp add --transport http codmir https://mcp.codmir.com/
```

## Other open source

| Repository | What it holds |
| ---------- | ------------- |
| [`sdk`](https://github.com/codmir-labs/sdk) | `@codmir/sdk`: error tracking, tracing, session replay and bug reporting |
| [`mcp`](https://github.com/codmir-labs/mcp) | `@codmir/mcp`: the local MCP server |
| [`mcp-plugin-anthropic`](https://github.com/codmir-labs/mcp-plugin-anthropic) | The Claude Code plugin for the hosted connector |
| [`skill`](https://github.com/codmir-labs/skill) and [`skills`](https://github.com/codmir-labs/skills) | Instructions for AI agents that set up Codmir in a project |
| [`example`](https://github.com/codmir-labs/example) | A small app that shows what the SDK captures |

## License

[MIT](LICENSE)
