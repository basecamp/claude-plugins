# 37signals agent plugins

[Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins)
marketplace for Basecamp, HEY, and Fizzy — skills, hooks, and commands that
let Claude interact with your 37signals products. We also share our internal
development skills as plugins.

```
claude plugin marketplace add basecamp/plugins
claude plugin install <plugin-name>
```

This repository was `basecamp/claude-plugins` until 2026-10-12. GitHub
redirects the old name, and the marketplace is still `37signals`, so existing
installs keep working.

## Cursor

`.cursor-plugin/marketplace.json` lists the Basecamp plugin for Cursor,
`plugins/cursor/basecamp`: Basecamp's official hosted MCP server at
`https://mcp.basecamp.com/mcp`, with no API key to configure. Cursor's
Marketplace also feeds Grok Bot. Install it from **Cursor Settings → Plugins**
once it's listed.

## Available plugins

| Plugin | Description |
|--------|-------------|
| [basecamp-cli](https://github.com/basecamp/basecamp-cli/tree/main/.claude-plugin) | Basecamp through the `basecamp` command, for Claude Code and Codex. Todos, cards, messages, files, schedule, check-ins, timeline, recordings, templates, webhooks, subscriptions, lineup, and campfire; links code to projects. |
| [hey](https://github.com/basecamp/hey-cli) | Read email, manage todos, track time. |
| [fizzy](https://github.com/basecamp/fizzy-cli) | Manage boards and cards, track work, link code to projects. |

### Pinned to releases

`basecamp-cli`, `hey` and `fizzy` install from their CLI's latest release, not
its default branch: a plugin's skills and hooks call the CLI you installed, and
you install that from a release. `release-pins.json` names each one's repo, and
its marketplace entry carries the `sha` of that release's commit.

Every hour, the Pin releases workflow runs `bin/pin-releases`, which moves each
pin to the newest release and never back, and opens a pull request when one
moved. Merging it ships that release's plugin. `bin/check-marketplace` fails
when a pinned plugin has no sha.

Claude Code updates an installed plugin only when its `plugin.json` version
changes, so a CLI's release has to stamp its version there for the pin to reach
existing installs.

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

The plugins with files here, `plugins/basecamp` (the hosted plugin for
Claude, not listed in the Claude marketplace) and `plugins/cursor/basecamp`
(the same server for Cursor), are mirrors. Their source of truth is
`plugins/claude/basecamp` and `plugins/cursor/basecamp` in the (private) Basecamp connector
repository, which tests it against the tools the connector actually serves.
Don't edit the mirror; change it upstream, then run
`bin/sync-basecamp-plugin <checkout>` to copy and validate it, and commit
with the source commit it prints. `bin/sync-basecamp-plugin --check
<checkout>` reports drift.
