# claude-toolkit

My Claude Code plugins: skills, agents and hooks I use on every computer.

## Plugins

| Plugin      | What it has                                  |
|-------------|----------------------------------------------|
| `personal`  | Personal tools and helpers                   |
| `work`      | Work tools: ClickUp, Linear, weekly reports   |
| `dev-tools` | Coding helpers: reviews, refactoring, git    |

## Install on a new computer

In Claude Code:

```text
/plugin marketplace add vcgtz/claude-toolkit
/plugin install personal@claude-toolkit
/plugin install work@claude-toolkit
/plugin install dev-tools@claude-toolkit
```

Get the latest changes:

```text
/plugin marketplace update claude-toolkit
```

## Develop and test locally

```bash
claude --plugin-dir ./plugins/personal --plugin-dir ./plugins/dev-tools
```

Run `/reload-plugins` after each change. Skills are called as `/<plugin>:<skill>`, for example `/personal:hello`. Agents show up in `/agents`.

## Add things

- **Skill:** `plugins/<plugin>/skills/<skill-name>/SKILL.md`
- **Agent:** `plugins/<plugin>/agents/<agent-name>.md`
- **Hooks:** `plugins/<plugin>/hooks/hooks.json`
- **MCP servers:** `plugins/<plugin>/.mcp.json` (use env vars for tokens, never commit secrets)
- **New plugin:** create `plugins/<name>/.claude-plugin/plugin.json` and add it to `.claude-plugin/marketplace.json`

Bump `version` in a plugin's `plugin.json` when you change it.
