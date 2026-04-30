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
