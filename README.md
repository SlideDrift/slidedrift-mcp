<p align="center"><img src="assets/slidedrift-icon.png" width="72" height="72" alt="SlideDrift"></p>

# SlideDrift MCP

Turn what you know into LinkedIn posts in your brand, from your AI assistant.

SlideDrift is a LinkedIn content studio. Connect its remote MCP server and your assistant can turn a link, your notes or an idea into an editable carousel or post in your brand, then export it or schedule it to LinkedIn. Nothing is created, exported or posted without your approval.

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=slidedrift&config=eyJ1cmwiOiJodHRwczovL3NsaWRlZHJpZnQuY29tL21jcCJ9)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Server-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=slidedrift&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fslidedrift.com%2Fmcp%22%7D)
[![SlideDrift MCP on Glama](https://glama.ai/mcp/connectors/com.slidedrift/mcp/badges/score.svg)](https://glama.ai/mcp/connectors/com.slidedrift/mcp)

## Server

```text
https://slidedrift.com/mcp
```

Remote, streamable HTTP, OAuth 2.1 with dynamic client registration. There is no API key: the first time you use it, you sign in to SlideDrift (or create a free account) and choose **Allow connection**.

## What you can ask

```text
Turn this article into a LinkedIn carousel: <link>
Make a 7-slide carousel from these notes
Plan four weeks of LinkedIn posts from my newsletter
Change the headline on slide 3 of my newest carousel
Export my newest carousel as a PDF
Schedule this carousel to my LinkedIn for Tuesday at 9am
```

Your assistant shows the credit cost and waits for your approval before it creates or exports anything, then gives you a link to open the result in the SlideDrift editor. Scheduling needs its own approval and a paid plan or trial.

## Set it up

**Claude (claude.ai, Desktop):** Settings, Connectors, Add custom connector, then paste `https://slidedrift.com/mcp`. SlideDrift is also in the Claude connector directory.

**Claude Code:**

```bash
claude mcp add --transport http slidedrift https://slidedrift.com/mcp
```

**ChatGPT:** add a custom connector (in developer mode) with `https://slidedrift.com/mcp`.

**Cursor:** use the button above, or add this to `.cursor/mcp.json`:

```json
{ "mcpServers": { "slidedrift": { "url": "https://slidedrift.com/mcp" } } }
```

**VS Code:** use the button above, or add to `.vscode/mcp.json`:

```json
{ "servers": { "slidedrift": { "type": "http", "url": "https://slidedrift.com/mcp" } } }
```

**Gemini CLI:**

```bash
gemini extensions install https://github.com/SlideDrift/slidedrift-mcp
```

**Agent skill (skills.sh):** the skill teaches an agent when and how to use SlideDrift.

```bash
npx skills add SlideDrift/slidedrift-mcp
```

**Clients that only speak stdio:**

```bash
npx -y mcp-remote@0.16.7 https://slidedrift.com/mcp --transport http-only
```

## What's in this repo

| File | For |
| --- | --- |
| `skills/slidedrift/SKILL.md` | Agent skill: skills.sh, ClawHub, Hermes, Gemini, Cursor |
| `.mcp.json` | Claude Code and Cursor (remote HTTP) |
| `mcp.json`, `plugin.json` | Hermes Agent plugin (through mcp-remote) |
| `gemini-extension.json`, `GEMINI.md` | Gemini CLI extension |
| `.cursor-plugin/plugin.json`, `.claude-plugin/plugin.json` | Cursor Directory and Claude Code plugin metadata |
| `lhm.plugin.json` | LobeHub marketplace |
| `server.json` | Official MCP registry entry (`com.slidedrift/mcp`) |

No server code lives here: SlideDrift's MCP server is hosted at `https://slidedrift.com/mcp`.

## Privacy and data

Tool calls go to slidedrift.com and act only on your own SlideDrift work. Some tools spend SlideDrift credits, always after you approve the quote. Scheduling publishes posts to LinkedIn on your behalf, and only after you approve. You can revoke the connection at any time from SlideDrift's settings or your assistant. When you use the `mcp-remote` bridge, it stores its OAuth tokens on your machine in `~/.mcp-auth`.

## Links

- Developer page: https://slidedrift.com/developers/mcp
- MCP docs: https://slidedrift.com/docs/integrations/mcp
- JSON API (same operations): https://slidedrift.com/developers/api
- SlideDrift: https://slidedrift.com

License: MIT (this repo's files).
