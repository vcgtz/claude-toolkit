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

## Install and update

Claude Code in the terminal and the Claude Code desktop app read the same configuration
(`~/.claude/settings.json`). Set this up once per computer, and both see the same plugins.

### 1. Add the marketplace (once per computer)

From a terminal:

```bash
claude plugin marketplace add vcgtz/claude-toolkit
```

Or, inside a Claude Code session in the terminal: `/plugin marketplace add vcgtz/claude-toolkit`.

The desktop app shows plugins from marketplaces that are already added, so add the marketplace from
the terminal first.

### 2. Install the plugins

**Terminal:**

```bash
claude plugin install dev-tools@claude-toolkit
claude plugin install personal@claude-toolkit
```

**Desktop app** (local or SSH session): click **+** next to the prompt box → **Plugins** →
**Add plugin**, and pick the plugin from the `claude-toolkit` list. Use **Manage plugins** to enable,
disable or uninstall a plugin.

Plugins are installed for your user by default, so they work in every project, in both apps.

### 3. Use them

- **Terminal:** type `/` and the skill name, for example `/dev-tools:review 123`.
- **Desktop app:** type `/` in the prompt box, or click **+** → **Slash commands**, and pick the skill.
- Plugins do not work in cloud sessions (desktop app cloud sessions or Claude Code on the web).

### 4. Get updates

```bash
claude plugin marketplace update claude-toolkit
claude plugin update dev-tools@claude-toolkit
claude plugin update personal@claude-toolkit
```

Then restart Claude Code in the terminal, and quit and reopen the desktop app.

### Check what is installed

```bash
claude plugin marketplace list
claude plugin list
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
