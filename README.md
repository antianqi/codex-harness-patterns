# codex-harness-patterns

> **Standalone mirror.** This repo contains exactly one Plugin from
> [MiniMax-AI/MiniMax-Code-Plugins](https://github.com/MiniMax-AI/MiniMax-Code-Plugins) — the
> `codex-harness-patterns` Plugin — without the surrounding registry, the validator, the
> example plugins, or the docs.
>
> It is the personal-repo side of the contribution: the **plugin itself** lives here, versioned
> and released; the **PR to the official registry** lives in
> [`antianqi/MiniMax-Code-Plugins-1`](https://github.com/antianqi/MiniMax-Code-Plugins-1).
> See [PR #18](https://github.com/MiniMax-AI/MiniMax-Code-Plugins/pull/18) for the official
> contribution.

A focused collection of Skills distilled from the **OpenAI Codex harness v0.149.0** execution
model (`codex-rs/core/`). These Skills teach a MiniMax Code agent how to survive long-running
multi-step tasks without losing focus, blowing its token budget, stalling on serial work,
shipping unverified changes, or burning context on bad sub-agent briefs.

## Releases

| Version | What it ships | When |
|---|---|---|
| [`v0.2.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.2.0) | 8 Skills (current) | 2026-08-24 |
| [`v0.1.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.1.0) | 4 Skills (initial) | 2026-08-24 |

See the [Releases page](https://github.com/antianqi/codex-harness-patterns/releases) for full
notes.

## What this Plugin adds (v0.2.0)

Eight Skills, all Skill-only (no MCP server, no network access):

| Skill | When to activate |
|---|---|
| `tool-output-budget` | A tool returns output you suspect is too large to keep verbatim (large logs, JSON, fetched HTML, minified files). |
| `context-pressure-compact` | The task is multi-step and long; the running `todowrite` exceeds 5 items, or the agent has been reasoning for many turns. |
| `parallel-fanout` | The user task is clearly decomposable into 2+ independent sub-tasks (independent files, independent probes, independent analyses). |
| `plan-stream-emit` | The user task is non-trivial and the user has not yet approved a plan; emit a structured plan before touching files. |
| `review-mode` | A non-trivial sub-task has just finished and the work is about to be marked done; the user wants verification before relying on the result. |
| `delegate-with-context` | About to call `task` to hand off a sub-task; the full conversation history is too large to forward and a minimal-context brief would do. |
| `world-state-tracking` | The task is long enough that the agent has lost the thread at least once, or `context-pressure-compact` is about to be applied. |
| `background-task` | A command is expected to take > 30 seconds, or the user wants a long-running process to coexist with ongoing work. |

## How to use this Plugin

You have two paths:

### Path A — install from the official registry (recommended)

This Plugin is published in
[`MiniMax-AI/MiniMax-Code-Plugins`](https://github.com/MiniMax-AI/MiniMax-Code-Plugins) under
`plugins/antianqi/codex-harness-patterns`. Once the official PR is merged, you can install it
from MiniMax Code's `/plugins` UI by searching for the contributor `antianqi` and the plugin
`codex-harness-patterns`.

### Path B — install from this standalone repo

1. Clone this repo:
   ```bash
   git clone https://github.com/antianqi/codex-harness-patterns.git
   cd codex-harness-patterns
   git checkout v0.2.0   # or the latest release
   ```
2. Copy `skills/` into your own copy of MiniMax-Code-Plugins under
   `plugins/<your-github-username>/codex-harness-patterns/skills/`, then add the matching
   `plugin.json`, `README.md`, and `LICENSE` from this repo at the parent level.
3. Open a PR from your fork to the official repo (so the Plugin is discoverable from the
   registry, not just from this repo).

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
    ├── plan-stream-emit/
    ├── review-mode/
    ├── delegate-with-context/
    ├── world-state-tracking/
    └── background-task/
```

## Versioning

This repo follows [Semantic Versioning](https://semver.org/) for the **Plugin**, not for
the MiniMax Code platform. A bump of the major version here means at least one Skill has
changed its contract (different `When to use` / different `Process`); a minor bump means
new Skills were added; a patch bump means documentation / examples / frontmatter were fixed.

## License

Apache-2.0 (same as the host repository `MiniMax-AI/MiniMax-Code-Plugins`).
