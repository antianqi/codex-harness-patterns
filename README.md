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
shipping unverified changes, burning context on bad sub-agent briefs, drifting from the
original goal, paying main-model prices for cheap-model work, losing track of which
sub-agent is doing what, failing on transient errors, reading streaming output, or losing
work at session end.

## Releases

| Version | What it ships | When |
|---|---|---|
| [`v0.6.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.6.0) | 18 Skills (current) | 2026-08-24 |
| [`v0.5.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.5.0) | 14 Skills | 2026-08-24 |
| [`v0.4.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.4.0) | 12 Skills | 2026-08-24 |
| [`v0.3.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.3.0) | 10 Skills | 2026-08-24 |
| [`v0.2.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.2.0) | 8 Skills | 2026-08-24 |
| [`v0.6.2`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.6.2) | 18 Skills (patch: catalog corrections + roadmap) | 2026-08-24 |
| [`v0.6.1`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.6.1) | 18 Skills (frontmatter rewrite) | 2026-08-24 |
| [`v0.6.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.6.0) | 18 Skills | 2026-08-24 |
| [`v0.5.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.5.0) | 14 Skills | 2026-08-24 |
| [`v0.4.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.4.0) | 12 Skills | 2026-08-24 |
| [`v0.3.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.3.0) | 10 Skills | 2026-08-24 |
| [`v0.2.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.2.0) | 8 Skills | 2026-08-24 |
| [`v0.1.0`](https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.1.0) | 4 Skills (initial) | 2026-08-24 |

See the [Releases page](https://github.com/antianqi/codex-harness-patterns/releases) for full
notes.

## v0.6.2 (this release) — patch

> **Skill 主体不变**(18 个 0.x.y 版本号不变) · 元数据 + 文档更新

这次 v0.6.2 是个"诚实记录"型 patch — 复盘发现 Plugin 实际只覆盖了 Codex 模式库的 ~60%,并启动 2-3 月系统性补完计划。

### What changed

- **`plugin.json`**:version `0.6.1` → `0.6.2`
- **CATALOG §7 修正**:`P-49 Fork` / `P-50 Rollback` / `P-51 Recover` / `P-52 History Mode` 从 ⛔"范围外"改 🟡"待深读" — 实际实现是 `codex-rs/thread-store/` 40+ 文件
- **CATALOG §8 修正**:`P-63 Skills runtime` / `P-64 Memory system` 从 ❌"不在 4 个重点"改 🟡"待深读" — **直接对应我们 Plugin 自身结构**
- **CATALOG §9 新增**:`research-log/2026-08-24-resurvey-findings.md` 列出 ~100 个未研究模式草案,挑选 50+ 高价值列入
- **RESEARCH-ROADMAP.md** 新建:2-3 月系统性补完计划(阶段 0-4)
- **6 篇纠错笔记** 新建:`knowledge/P-{49,50,51,52,63,64}-*.md`

### What did NOT change

- 18 skill 主体(版本号全部不变)
- 18 skill frontmatter(不动)
- 18 skill 的输出契约 / 验证清单(不动)

### What comes next

- v0.7.0:周 1-4 深读 5 大核心 crate(memories / skills / thread-store / core-plugins / prompts)
- v0.8.0:周 5-8 次重要 crate(core/agent / core/session / tools / rollout / models-manager / protocol)
- v0.9.0:周 9-10 边角 crate 收口
- v1.0.0:阶段 4 — 5 个新 skill(long-term-memory / skill-auto-select / plugin-author-helper / tool-discovery-pattern / session-branch-fork) + Plugin 大版本

## What this Plugin adds (v0.6.0, 18 Skills)

| # | Skill | When to activate |
|---|---|---|
| 1 | `tool-output-budget` | A tool returns output you suspect is too large to keep verbatim (large logs, JSON, fetched HTML, minified files). |
| 2 | `context-pressure-compact` | The task is multi-step and long; the running `todowrite` exceeds 5 items, or the agent has been reasoning for many turns. |
| 3 | `parallel-fanout` | The user task is clearly decomposable into 2+ independent sub-tasks (independent files, independent probes, independent analyses). |
| 4 | `plan-stream-emit` | The user task is non-trivial and the user has not yet approved a plan; emit a structured plan before touching files. |
| 5 | `review-mode` | A non-trivial sub-task has just finished and the work is about to be marked done; the user wants verification before relying on the result. |
| 6 | `delegate-with-context` | About to call `task` to hand off a sub-task; the full conversation history is too large to forward and a minimal-context brief would do. |
| 7 | `world-state-tracking` | The task is long enough that the agent has lost the thread at least once, or `context-pressure-compact` is about to be applied. |
| 8 | `background-task` | A command is expected to take > 30 seconds, or the user wants a long-running process to coexist with ongoing work. |
| 9 | `goal-persistence` | A non-trivial task has just been stated (set the goal); the user has redirected (update the goal); or a `context-pressure-compact` is about to be applied (alignment check). |
| 10 | `model-router` | About to call `task` for a non-trivial sub-task, or about to spend the main model on work a cheaper model could do. |
| 11 | `completion-audit` | About to say "done" / "complete" / "ship it" on a non-trivial task. Derives requirements, identifies authoritative evidence, verifies each. |
| 12 | `fork-context-decision` | About to call `task` to hand off a sub-task. Decides how much parent context to give the sub-agent via the `fork_turns` parameter. |
| 13 | `subagent-family-tracking` | Spawned a sub-agent (or have one running). Track the parent/child tree so you do not lose children, duplicate work, or leave anyone running. |
| 14 | `goal-token-budgeting` | The user set an explicit `token_budget` on a goal. Track running usage against the budget and report the final number on completion. |
| 15 | `error-recovery-strategy` | A tool call, sub-agent task, or external operation failed. Decide between retry / switch / fallback / ask-user / skip. |
| 16 | `retry-with-backoff` | About to retry a `transient` error. State the policy first: max attempts, base delay, max delay, jitter, total time budget. |
| 17 | `streaming-output-reader` | A tool returns a long stream (SSE / WebSocket / `tail -f` / large log). Read in bounded chunks, synthesize, never loop. |
| 18 | `session-handoff` | The session is ending (user stepping away, time up, about to compact). Write a handoff file so next session can pick up in 30 seconds. |

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
   git checkout v0.6.0   # or the latest release
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
├── plugin.json        ← manifest for the Plugin (name = codex-harness-patterns, version 0.6.0)
└── skills/
    ├── tool-output-budget/
    ├── context-pressure-compact/    (v1.0)
    ├── parallel-fanout/             (v1.0)
    ├── plan-stream-emit/
    ├── review-mode/
    ├── delegate-with-context/       (v1.0)
    ├── world-state-tracking/
    ├── background-task/
    ├── goal-persistence/            (v1.0)
    ├── model-router/
    ├── completion-audit/
    ├── fork-context-decision/
    ├── subagent-family-tracking/
    ├── goal-token-budgeting/
    ├── error-recovery-strategy/     (new in v0.6.0)
    ├── retry-with-backoff/          (new in v0.6.0)
    ├── streaming-output-reader/     (new in v0.6.0)
    └── session-handoff/             (new in v0.6.0)
```

## Versioning

This repo follows [Semantic Versioning](https://semver.org/) for the **Plugin**, not for
the MiniMax Code platform. A bump of the major version here means at least one Skill has
changed its contract (different `When to use` / different `Process`); a minor bump means
new Skills were added; a patch bump means documentation / examples / frontmatter were fixed.

## License

Apache-2.0 (same as the host repository `MiniMax-AI/MiniMax-Code-Plugins`).
