# 37signals Claude Code Plugins

[Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins)
marketplace for Basecamp, HEY, and Fizzy — skills, hooks, and commands that
let Claude interact with your 37signals products.

```
claude plugin marketplace add basecamp/claude-plugins
claude plugin install <plugin-name>
```

## Available plugins

| Plugin | Product | Description |
|--------|---------|-------------|
| [basecamp](https://github.com/basecamp/basecamp-cli/tree/main/.claude-plugin) | Basecamp | Todos, cards, messages, files, schedule, check-ins, timeline, recordings, templates, webhooks, subscriptions, lineup, and campfire. |

HEY and Fizzy plugins coming soon.

## About

This repo is a thin marketplace index. Plugin source code (skills, hooks,
commands) lives in each product's CLI repo. To contribute, open issues or PRs
there.
