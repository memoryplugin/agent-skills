# MemoryPlugin Agent Skills

**One memory. Every AI.**

This repo teaches AI agents to actually use your long-term memory: recall what they need before assuming, and store what matters before finishing. It works with [MemoryPlugin](https://www.memoryplugin.com), the memory layer you keep across ChatGPT, Claude, Gemini, Cursor, and 20+ other AI tools.

Adding a memory MCP server to an agent is not enough. Left to themselves, agents answer "you know my preferences" from guesswork and reply "let me know if you want me to remember that" instead of remembering. This skill fixes both, with the habits of heavy MemoryPlugin users built in: targeted recall, atomic dated memories, topical buckets, snapshot memories for long-running work, and cross-tool chat history recall.

Full overview, install matrix, and FAQ: [memoryplugin.com/agent-skill](https://www.memoryplugin.com/agent-skill).

## Install

### Claude Code (recommended: plugin, one install gets everything)

```
/plugin marketplace add memoryplugin/agent-skills
/plugin install memoryplugin@memoryplugin
```

The plugin bundles the skill, the MemoryPlugin MCP server config (OAuth sign-in in the browser, no API keys), and a session-start reminder so the agent uses memory without being told.

### Any agent that supports skills (Codex, Cursor, Copilot, Gemini CLI, Amp, opencode, Goose, and more)

```bash
npx skills add memoryplugin/agent-skills
```

Then connect the MemoryPlugin MCP server for your client: see [skills/memoryplugin/references/setup.md](skills/memoryplugin/references/setup.md).

### Claude (web and desktop)

1. Connect the connector: Settings, Connectors, "Add custom connector", paste `https://www.memoryplugin.com/api/mcp/mcp`.
2. Upload the skill: download `memoryplugin-skill.zip` from [Releases](https://github.com/memoryplugin/agent-skills/releases), then Settings, Capabilities, Skills, "Upload skill".

## What the skill does

- **Recall before assuming.** Targeted memory search with the task's concrete nouns at task start, category summaries for broad orientation, and chat history recall when you reference a past conversation from any AI tool.
- **Store before finishing.** Preferences with the why, decisions with the rationale, project snapshots at milestones, corrections when reality changes. Atomic, dated, filed into the right bucket, with a one-line receipt so you can veto anything.
- **Knows what not to store.** No secrets, no transient debugging noise, no repo conventions (those belong in CLAUDE.md or AGENTS.md).

## Requirements

A MemoryPlugin account: https://www.memoryplugin.com. The MCP server authenticates with OAuth in the browser; no keys to manage.

## License

MIT
