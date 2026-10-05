# 37signals Claude Code Plugins

[Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins)
marketplace for Basecamp, HEY, and Fizzy — skills, hooks, and commands that
let Claude interact with your 37signals products. We also share our internal
development skills as plugins.

```
claude plugin marketplace add basecamp/claude-plugins
claude plugin install <plugin-name>
```

## Available plugins

| Plugin | Description |
|--------|-------------|
| [basecamp](plugins/basecamp) | Basecamp through its hosted connector, for claude.ai chat, Cowork, and Claude Code. Six workflows: catch up, weekly recap, triage Hey!, plan a project, draft a check-in, prep a meeting. |
| [basecamp-cli](https://github.com/basecamp/basecamp-cli/tree/main/.claude-plugin) | Basecamp through the `basecamp` command, for Claude Code and Codex. Todos, cards, messages, files, schedule, check-ins, timeline, recordings, templates, webhooks, subscriptions, lineup, and campfire; links code to projects. |
| [hey](https://github.com/basecamp/hey-cli) | Read email, manage todos, track time. |
| [fizzy](https://github.com/basecamp/fizzy-cli) | Manage boards and cards, track work, link code to projects. |

### Which Basecamp plugin?

- **`basecamp`** talks to Basecamp's hosted connector at
  `https://mcp.basecamp.com/mcp`. Nothing to install beyond the plugin: you
  connect your Basecamp account from the plugin's Connectors tab. It's the
  same plugin Anthropic's directory lists, and the only one that works in
  claude.ai chat and Cowork.
- **`basecamp-cli`** drives the [`basecamp` CLI](https://github.com/basecamp/basecamp-cli)
  on your machine. Pick it for terminal work in Claude Code or Codex:
  scripting, full API coverage, and linking commits and branches to
  Basecamp. It needs the CLI installed and signed in.

You can have both; they don't share state.

### Moving from the old `basecamp` plugin

Until October 2026, `basecamp@37signals` was the CLI plugin. It's now
`basecamp-cli@37signals`, and `basecamp@37signals` is the hosted plugin. If
you installed the CLI plugin before the rename, switch to its new name:

```
claude plugin marketplace update 37signals
claude plugin uninstall basecamp@37signals
claude plugin install basecamp-cli@37signals
```

Then install `basecamp@37signals` as well if you want the hosted one.

## Development plugins

| Plugin | Description |
|--------|-------------|
| [dev](https://github.com/basecamp/house-skills/tree/main/plugins/dev) | AI-assisted development workflow — PR reviews, plan-implement loops, and expert consultation. |
| [security](https://github.com/basecamp/house-skills/tree/main/plugins/security) | GitHub Actions pipeline hardening and CI security. |
| [ai](https://github.com/basecamp/house-skills/tree/main/plugins/ai) | Crafting agent skills and writing install documentation for autonomous execution. |
| [recap](https://github.com/basecamp/house-skills/tree/main/plugins/recap) | Activity digests — pluggable source fetchers, timescale synthesis, audience-aware composition. |

## About

This repo is mostly a thin marketplace index. Plugin source code (skills,
hooks, commands) lives in each product's own repo. To contribute, open issues
or PRs there.

The one plugin with files here, `plugins/basecamp`, is a mirror. Its source
of truth is `plugins/claude/basecamp` in the (private) Basecamp connector
repository, which tests it against the tools the connector actually serves.
Don't edit the mirror; change it upstream, then run
`bin/sync-basecamp-plugin <checkout>` to copy and validate it, and commit
with the source commit it prints. `bin/sync-basecamp-plugin --check
<checkout>` reports drift.
