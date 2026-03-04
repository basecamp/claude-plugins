# Claude Code Plugins for Basecamp

[Claude Code plugin](https://docs.anthropic.com/en/docs/claude-code/plugins)
marketplace for Basecamp — skills, hooks, and commands that let Claude interact
with your Basecamp workspace.

```
claude plugin marketplace add basecamp/claude-plugins
claude plugin install basecamp
```

## Available plugins

| Plugin | Description |
|--------|-------------|
| [basecamp](https://github.com/basecamp/basecamp-cli/tree/main/.claude-plugin) | Basecamp integration — todos, cards, messages, files, schedule, check-ins, timeline, recordings, templates, webhooks, subscriptions, lineup, and campfire. |

## Requires

- [Basecamp CLI](https://github.com/basecamp/basecamp-cli) (`brew install basecamp/tap/basecamp` or see [install instructions](https://github.com/basecamp/basecamp-cli#installation))
- An authenticated Basecamp account (`basecamp login`)

## About

This repo is a thin marketplace index. Plugin source code (skills, hooks,
commands) lives in [basecamp/basecamp-cli](https://github.com/basecamp/basecamp-cli).
To contribute, open issues or PRs there.
