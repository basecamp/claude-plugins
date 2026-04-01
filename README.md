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
| [basecamp](https://github.com/basecamp/basecamp-cli/tree/main/.claude-plugin) | Todos, cards, messages, files, schedule, check-ins, timeline, recordings, templates, webhooks, subscriptions, lineup, and campfire. |

HEY and Fizzy plugins coming soon.

## Development plugins

| Plugin | Description |
|--------|-------------|
| [dev](https://github.com/basecamp/house-skills/tree/main/plugins/dev) | AI-assisted development workflow — PR reviews, plan-implement loops, and expert consultation. |
| [security](https://github.com/basecamp/house-skills/tree/main/plugins/security) | GitHub Actions pipeline hardening and CI security. |
| [ai](https://github.com/basecamp/house-skills/tree/main/plugins/ai) | Crafting agent skills and writing install documentation for autonomous execution. |
| [recap](https://github.com/basecamp/house-skills/tree/main/plugins/recap) | Activity digests — pluggable source fetchers, timescale synthesis, audience-aware composition. |

## About

This repo is a thin marketplace index. Plugin source code (skills, hooks,
commands) lives in each product's CLI repo. To contribute, open issues or PRs
there.
