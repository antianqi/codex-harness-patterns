# Changelog

## v0.5.0 (2026-08-24)

Added two Skills that close the sub-agent ecology loop:

- `subagent-family-tracking` — track the parent/child thread tree of
  spawned sub-agents so you do not lose children, duplicate work, or
  leave anyone running. Mirrors `codex-rs/agent-graph-store/`
  (`ThreadSpawnEdgeStatus` Open/Closed).
- `goal-token-budgeting` — when the user sets an explicit `token_budget`
  on a goal, track running usage, surface at 50%/80%/100% thresholds,
  stop at 100% and ask. Mirrors `ext/goal/src/accounting.rs`
  (GoalAccountingState) and the "Tokens used / Token budget / Tokens
  remaining" section of the goal continuation template.

Updated two Skills to v1.0 based on deeper reads of the Codex source:

- `context-pressure-compact` v1.0 — added the 64K retention budget
  concept from `compact_remote_v2.rs::RETAINED_MESSAGE_TOKEN_BUDGET`.
  Snapshots now report the retained token estimate and the
  "discarded N tool calls / M lines" count. Cross-referenced all five
  persistent-state files (goal / world-state / family / usage-log /
  todowrite) so the snapshot is the single coordination point.
- `delegate-with-context` v1.0 — added the V2 message envelope
  (Message Type / Task name / Sender / Payload) so sub-agent replies
  are parsed consistently. Added explicit "return path" section in the
  brief. Cross-referenced `fork-context-decision`, `model-router`, and
  `subagent-family-tracking`.

Total Skills: 14 (12 from v0.4.0 + 2 new + 2 skill upgrades to v1.0).

## v0.4.0 (2026-08-24)

Added two Skills extracted from the Codex continuation template and the
V2 multi-agent protocol:

- `completion-audit` — before declaring a non-trivial task done, derive
  requirements, identify authoritative evidence, verify against the
  actual current state, and only declare done when every requirement
  has its own ✅. Mirrors the completion-audit section of the Codex
  goal continuation template.
- `fork-context-decision` — pick `all` / `N` / `none` for `fork_turns`
  explicitly, not by default. Mirrors the `fork_turns` semantics in
  Codex's V2 multi-agent protocol.

Updated two Skills to v1.0:

- `goal-persistence` v1.0 — completion-audit and blocked-audit
  sections, token-budget reporting rule, "treat completion as
  unproven" alignment.
- `parallel-fanout` v1.0 — explicit-spawn principle (P-20:
  opt-in, not auto), `max_concurrency` awareness.

Total Skills: 12.

## v0.3.0 (2026-08-24)

Added two Skills that close the long-running task loop:

- `goal-persistence` — north-star goal file, drift self-test.
- `model-router` — classify sub-task as cheap/medium/main.

Total Skills: 10.

## v0.2.0 (2026-08-24)

Added four Skills that round out the long-running task toolkit:

- `review-mode` — switch to critic mode, PASS/FIX/REDO.
- `delegate-with-context` — minimal-context brief for `task()`.
- `world-state-tracking` — state file that survives compaction.
- `background-task` — long-running commands in the background.

Total Skills: 8.

## v0.1.0 (2026-08-24) — initial release

Four Skills:

- `tool-output-budget` — token-aware head+tail+marker truncation.
- `context-pressure-compact` — structured snapshot.
- `parallel-fanout` — independent sub-task dispatch.
- `plan-stream-emit` — todowrite-shaped plan.
