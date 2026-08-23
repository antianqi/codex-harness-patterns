# codex-harness-patterns

> **v0.1.0** — initial release. See [CHANGELOG.md](CHANGELOG.md) for the roadmap to v0.2.0.

A focused collection of Skills distilled from the **OpenAI Codex harness v0.149.0** execution
model (`codex-rs/core/`). These Skills teach a MiniMax Code agent how to survive long-running
multi-step tasks without losing focus, blowing its token budget, or stalling on serial work.

## What this Plugin adds (v0.1.0)

Four Skills, all Skill-only (no MCP server, no network access):

| Skill | When to activate |
|---|---|
| `tool-output-budget` | A tool returns output you suspect is too large to keep verbatim (large logs, JSON, fetched HTML, minified files). |
| `context-pressure-compact` | The task is multi-step and long; the running `todowrite` exceeds 5 items, or the agent has been reasoning for many turns. |
| `parallel-fanout` | The user task is clearly decomposable into 2+ independent sub-tasks (independent files, independent probes, independent analyses). |
| `plan-stream-emit` | The user task is non-trivial and the user has not yet approved a plan; emit a structured plan before touching files. |

## Requirements

- **MiniMax Code** with Agent Plugins 1.0 support.
- **No Python, no Node, no external services.** These Skills are pure Markdown instructions.
- **No MCP server, no network, no credentials.**

## How to use this Plugin

You have two paths:

### Path A — install from the official registry (recommended)

This Plugin is published in
[`MiniMax-AI/MiniMax-Code-Plugins`](https://github.com/MiniMax-AI/MiniMax-Code-Plugins) under
`plugins/antianqi/codex-harness-patterns`.

### Path B — install from this standalone repo

1. Clone this repo:
   ```bash
   git clone https://github.com/antianqi/codex-harness-patterns.git
   cd codex-harness-patterns
   git checkout v0.1.0
   ```
2. Copy `skills/` into your own copy of MiniMax-Code-Plugins under
   `plugins/<your-github-username>/codex-harness-patterns/skills/`, then add the matching
   `plugin.json`, `README.md`, and `LICENSE` from this repo at the parent level.
3. Open a PR from your fork to the official repo.

## File layout

```
codex-harness-patterns/
├── README.md          ← you are here
├── CHANGELOG.md       ← version history
├── LICENSE            ← Apache-2.0
├── plugin.json        ← manifest for the Plugin (name = codex-harness-patterns)
└── skills/
    ├── tool-output-budget/
    ├── context-pressure-compact/
    ├── parallel-fanout/
    └── plan-stream-emit/
```

## License

Apache-2.0
