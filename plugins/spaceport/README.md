# Spaceport Plugin for Claude Code

Add Spaceport framework expertise to any existing Spaceport project. Provides six specialized agents and full framework documentation as reference.

## What You Get

- **Six agents** that understand Spaceport's APIs, conventions, and best practices
- **Complete framework documentation** bundled as agent reference material
- **Zero project modification** — attaches externally, doesn't change your files

## Agents

| Agent | Type | Purpose |
|---|---|---|
| **Spaceport Consultant** | Advisory | Framework authority — validates code and plans against documentation |
| **Routing** | Advisory | `@Alert` patterns, route creation, middleware, auth plugs |
| **Launchpad** | Advisory | `.ghtml` templates, server elements, server actions, reactive bindings |
| **Data Modeling** | Advisory | Documents, views, migrations, Cargo, Row/Value pattern |
| **CouchDB Probe** | Operational | Direct HTTP calls to verify database state |
| **Spaceport Dev Probe** | Operational | Screen session access to dev server logs, route testing |

## Installation

From your Spaceport project directory, in Claude Code:

```
/plugin marketplace add spaceport-dev/claude-spaceport-support
/plugin install spaceport@spaceport-support
```

The first command registers this repo as a plugin marketplace. The second installs the `spaceport` plugin from it. After install, restart Claude Code to load the agents.

To update later:

```
/plugin marketplace update spaceport-support
```

## When to Use This vs. create-spaceport-app

- **This plugin** — for existing Spaceport projects. Agents discover project context by reading `config.spaceport` at runtime.
- **[create-spaceport-app](https://github.com/spaceport-dev/create-spaceport-app)** — for new projects. Clone it, run the bootstrap, and get project-specific agents with your config baked in.

If your project was bootstrapped from create-spaceport-app, you already have project-specific agents in `.claude/agents/` — this plugin is redundant. The agents will detect this and warn you.

## Requirements

- A Spaceport project with `config.spaceport` in the root
- CouchDB running (for the CouchDB Probe agent)
- The dev server running in a screen session (for the Dev Probe agent)
