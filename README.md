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
| [basecamp-cli](https://github.com/basecamp/basecamp-cli/tree/main/.claude-plugin) | Basecamp through the `basecamp` command, for Claude Code and Codex. Todos, cards, messages, files, schedule, check-ins, timeline, recordings, templates, webhooks, subscriptions, lineup, and campfire; links code to projects. |
| [hey](https://github.com/basecamp/hey-cli) | Read email, manage todos, track time. |
| [fizzy](https://github.com/basecamp/fizzy-cli) | Manage boards and cards, track work, link code to projects. |

### `basecamp` is now `basecamp-cli`

The CLI plugin used to be `basecamp@37signals`. It's now
`basecamp-cli@37signals`, with the same source, skills and hooks. The
`basecamp` command itself keeps its name.

For a deprecation window (7 days from the CLI release that ships the rename), `basecamp` stays in this
marketplace as an alias with the same source as `basecamp-cli`. Existing
installs keep loading and updating. From the basecamp-cli release with the
rename on, a plugin installed under the old name says once that it has a
new name. `basecamp setup` moves you to `basecamp-cli`. To
do it by hand:

```
claude plugin marketplace update 37signals
claude plugin install basecamp-cli@37signals
claude plugin uninstall basecamp@37signals
```

The alias goes away in its own later PR, after the window.

### The hosted Basecamp plugin

`plugins/basecamp` is a second Basecamp plugin. It uses Basecamp's hosted
connector at `https://mcp.basecamp.com/mcp` rather than the CLI, so it also
works in claude.ai chat and Cowork. This is the folder Anthropic's plugin
directory publishes as `basecamp`.

This marketplace doesn't list it. `basecamp` here is the CLI alias until
the window ends, and only after that can the name point at the hosted
plugin. `bin/check-marketplace`, which CI runs, holds that rule: a
`basecamp` entry passes only with exactly the same source as
`basecamp-cli`. The script says when the rule can change.

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

The one plugin with files here, `plugins/basecamp` (the hosted plugin, not
listed in the marketplace), is a mirror. Its source
of truth is `plugins/claude/basecamp` in the (private) Basecamp connector
repository, which tests it against the tools the connector actually serves.
Don't edit the mirror; change it upstream, then run
`bin/sync-basecamp-plugin <checkout>` to copy and validate it, and commit
with the source commit it prints. `bin/sync-basecamp-plugin --check
<checkout>` reports drift.
