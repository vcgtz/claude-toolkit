# claude-toolkit

Claude Code plugins: skills, agents and hooks I use on every computer.

## Plugins

| Plugin      | What it has                                  |
|-------------|----------------------------------------------|
| `personal`  | Personal tools and helpers                   |
| `dev-tools` | Coding helpers: reviews, refactoring, git    |

### dev-tools

- **`/dev-tools:review [PR number | PR URL | branch]`**: principal-engineer code review. With no argument, it reviews the current branch plus uncommitted changes. It returns findings ordered by severity (🔴 Critical, 🟠 High, 🟡 Medium, 🔵 Low), each with the changed code, why it matters and a suggested fix. It runs the `code-reviewer` agent, which is read-only.
- **`code-reviewer` agent**: does the review. Claude can also use it on its own after finishing a code change.

## Install on a new computer

In Claude Code:

```text
/plugin marketplace add vcgtz/claude-toolkit
/plugin install personal@claude-toolkit
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
