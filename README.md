# Global Claude Marketplace

Private plugin marketplace for logan's Claude Code plugins. Canonical plugin names and sources are in [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json) (**18 plugins**: two custom, five mirrored “core” integrations, eleven Anthropic authoring / workflow helpers). This catalog aggregates **your own plugins** plus **curated mirrors** wired to upstream repositories (matching [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) where applicable). The marketplace declares `allowCrossMarketplaceDependenciesOn: ["claude-plugins-official"]` so installs can resolve dependencies against Anthropic's official catalog.

## Included plugins

**Custom**

| Plugin | What it does | When to install | Contents (skills, commands, hooks, agents, etc.) |
| --- | --- | --- | --- |
| **global-plugin** | ~25 guardrail skills for React/Next.js + NestJS + Prisma + AWS, plus `/init-mcp` and `/suggest-mod` slash commands | Default custom tooling for any consumer repo | [Repo](https://github.com/lgerard314/global-plugin); `git-subdir` → `plugin/` on `main` |
| **board** | Planning governance under `BOARD/plans/` — frontmatter, locked leaves, ADR promotion, `/board:*` | Claude-driven BOARD SPEC/PLAN / anti-staleness workflows | [Repo](https://github.com/lgerard314/board-plugin); hooks + slash commands |

**Curated**

| Plugin | What it does | When to install | Contents (skills, commands, hooks, agents, etc.) |
| --- | --- | --- | --- |
| **superpowers** | TDD, systematic debugging, brainstorming, subagent workflows, skill authoring habits | obra-style engineering discipline in-session | [obra/superpowers](https://github.com/obra/superpowers): skills tree, hooks, commands; full-repo `url` install |
| **frontend-design** | Production-grade frontend UI (layout, type, cohesion; avoids generic AI chrome) | Building or reviewing web UI | Anthropic monorepo [`frontend-design`](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/frontend-design): **skills** |
| **prisma** | Prisma MCP: Postgres, migrations, queries, connection management | Prisma / Prisma Postgres work with Claude | [prisma.io](https://prisma.io); [prisma/claude-plugin](https://github.com/prisma/claude-plugin); MCP in plugin tree; pinned **SHA** in `marketplace.json` |
| **deploy-on-aws** | AWS architecture, IaC, deploy paths, cost awareness | Designing or deploying to AWS via agent guidance | AWS Labs [`plugins/deploy-on-aws`](https://github.com/awslabs/agent-plugins/tree/main/plugins/deploy-on-aws): skills, hooks |
| **semgrep** | Secure coding oriented around Semgrep | You want vulnerability-aware edits with Semgrep in the loop | [`semgrep/mcp-marketplace`](https://github.com/semgrep/mcp-marketplace) `plugin/` subdir |

Anthropic authoring and workflow helpers (Agent SDK setup, MCP builder, **`/code-review`**, **`commit-commands`**, **`hookify`**, **`session-report`**, …) are listed in **[Additional Plugins](#additional-plugins)**—the same **`name`** values as in **`marketplace.json`**.

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
/plugin install prisma@global-plugins
```

## Update marketplace

```text
/plugin marketplace update
```
