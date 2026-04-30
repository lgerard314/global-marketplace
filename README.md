# Global Claude Marketplace

Private plugin marketplace for logan's Claude Code plugins. Entries live in [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json). This catalog lists **your own plugins** plus **curated mirrors** wired to upstream repositories (matching [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) where applicable). The marketplace also declares `allowCrossMarketplaceDependenciesOn: ["claude-plugins-official"]` so installs can resolve dependencies against Anthropic's official catalog.

## Included plugins

**Custom**

- **global-plugin** ([repo](https://github.com/lgerard314/global-plugin))
- **global-plugin-dev** — staging build pinned to `dev`; pre-promotion testing only
- **board** — planning governance under `BOARD/plans/` ([repo](https://github.com/lgerard314/board-plugin))

**Curated**

- **superpowers** — TDD, debugging, brainstorming, workflow skills ([obra/superpowers](https://github.com/obra/superpowers))
- **frontend-design** — production-grade frontend UI guidance ([Anthropic plugin tree](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/frontend-design))
- **prisma** — Prisma MCP (Postgres, migrations, queries) ([prisma.io](https://prisma.io); [repo](https://github.com/prisma/claude-plugin), pinned commit in marketplace)
- **deploy-on-aws** — AWS deployment, IaC, cost guidance ([awslabs/agent-plugins](https://github.com/awslabs/agent-plugins))
- **semgrep** — security-oriented coding support ([semgrep/mcp-marketplace](https://github.com/semgrep/mcp-marketplace))

Anthropic authoring and workflow helpers (SDK, hooks, MCP, PR review, commits, reporting) are mirrored in **[Additional Plugins](#additional-plugins)**.

## Additional Plugins

These entries are mirrored from Anthropic’s [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) monorepo (same sources as `/plugin install …@global-plugins`). Install only the ones whose workflows you want; omit heavy or overlapping plugins (for example skip **code-review** if you rarely use `/code-review`, or skip **hookify** if you already maintain `hooks.json` by hand).

| Plugin | What it does | When to install | Contents (skills, commands, hooks, agents, etc.) |
| --- | --- | --- | --- |
| [agent-sdk-dev](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/agent-sdk-dev) | Scaffold and verify Claude Agent SDK apps (Python / TypeScript) with guided setup | You build or audit agents against the Claude Agent SDK | **`/new-sdk-app`** command; verifier **agents** `agent-sdk-verifier-py`, `agent-sdk-verifier-ts` |
| [claude-code-setup](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-code-setup) | Read-only codebase scan that recommends MCPs, skills, hooks, subagents, slash workflows | Greenfield Claude Code hygiene or onboarding a repo | **Skill** `claude-automation-recommender`; natural-language prompts (no dedicated slash bundle) |
| [code-review](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-review) | Multi-agent GitHub PR review with confidence filtering | Non-trivial PRs on GitHub with `gh` available | **`/code-review`** command (parallel reviewer agents posted as PR comment) |
| [claude-md-management](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-md-management) | Keep `CLAUDE.md` tuned to the repo and capture session learnings | Drift in project memory or after long sessions | **Skill** `claude-md-improver`; **`/revise-claude-md`** command |
| [code-simplifier](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-simplifier) | Simplify recent edits while preserving behavior | Cleanup passes after iterative changes | **Agents** driven simplification workflows (focused on modified code) |
| [commit-commands](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/commit-commands) | Git commit / push / PR helpers | Daily git + GitHub flow from Claude Code | **`/commit`**, **`/commit-push-pr`**, **`/clean_gone`** commands |
| [example-plugin](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/example-plugin) | Reference layout for Claude Code plugins | Learning plugin structure or starting a fork | **Skills** (`example-skill`, `example-command`), **legacy** `commands/example-command.md`, **`.mcp.json`** sample MCP config |
| [hookify](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/hookify) | Author guard-rail hooks from chat or Markdown rules without hand-editing `hooks.json` | Policy enforcement (`rm -rf`, secrets, Stop gates) | **`/hookify`**, **`/hookify:list`**, **`/hookify:configure`**, **`/hookify:help`**; bundled **hooks** implementations; **`writing-rules`** skill; supporting **agents** |
| [mcp-server-dev](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/mcp-server-dev) | End-to-end guidance for MCP server design (HTTP, MCPB, local stdio, MCP UI apps) | Building or wrapping MCP tooling | **Skills** `build-mcp-server`, `build-mcp-app`, `build-mcpb`; slash **`/mcp-server-dev:build-mcp-server`** |
| [plugin-dev](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/plugin-dev) | Opinionated authoring for Claude plugins (hooks, MCP, agents, commands, …) | Any time you ship or refactor marketplace plugins | **Skills** `agent-development`, `command-development`, `hook-development`, `mcp-integration`, `plugin-settings`, `plugin-structure`, `skill-development` |
| [session-report](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/session-report) | HTML drill-down reports from local session transcripts (~/.claude/projects) | Capacity / cost tuning and usage review | **Skill** [`session-report`](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/session-report/skills/session-report/SKILL.md) plus bundled **`analyze-sessions.mjs`** and **`template.html`** |

## Add this marketplace

In Claude Code:

```text
/plugin marketplace add https://github.com/lgerard314/global-marketplace
```

## Install a plugin

The marketplace identifier is **global-plugins**. Use:

```text
/plugin install <plugin-name>@global-plugins
```

Examples:

```text
/plugin install global-plugin@global-plugins
/plugin install board@global-plugins
/plugin install superpowers@global-plugins
```

## Update marketplace

```text
/plugin marketplace update
```
