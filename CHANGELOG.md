# Changelog

## v0.6.0 (2026-08-24)

Added four Skills that close the **error / streaming / session-end loop**:

- `error-recovery-strategy` — 4-bucket classification (transient /
  deterministic / stale / unknown) → 5-action decision tree (retry /
  switch / fallback / refresh-then-retry / ask-user / skip). Mirrors
  the `code-mode` reconnect philosophy and `MultiAgentMode::ExplicitRequestOnly`
  opt-in principle.
- `retry-with-backoff` — explicit retry policy: max 3 attempts, base 2s,
  max 30s, full jitter, 60s total budget. Respects `Retry-After`. Hard
  ceiling, no silent extension.
- `streaming-output-reader` — read in bounded chunks (head / tail / grep),
  write a cumulative summary, stop after at most 3 reads.
- `session-handoff` — at session end, write a structured handoff file
  (verbatim goal, state references, done/in-progress, next step,
  critical paths, "might be wrong" risks). Mirrors `state/runtime/recovery.rs`
  and `rollout_migration_state` migration.

Total Skills: 18 (14 from v0.5.0 + 4 new).

## v0.5.0 (2026-08-24)

Added two Skills that close the sub-agent ecology loop:

- `subagent-family-tracking`
- `goal-token-budgeting`

Updated two Skills to v1.0:

- `context-pressure-compact` v1.0
- `delegate-with-context` v1.0

Total Skills: 14.

## v0.4.0 (2026-08-24)

Added two Skills:

- `completion-audit`
- `fork-context-decision`

Updated two Skills to v1.0:

- `goal-persistence` v1.0
- `parallel-fanout` v1.0

Total Skills: 12.

## v0.3.0 (2026-08-24)

Added two Skills:

- `goal-persistence`
- `model-router`

Total Skills: 10.

## v0.2.0 (2026-08-24)

Added four Skills:

- `review-mode`
- `delegate-with-context`
- `world-state-tracking`
- `background-task`

Total Skills: 8.

## v0.1.0 (2026-08-24) — initial release

Four Skills:

- `tool-output-budget`
- `context-pressure-compact`
- `parallel-fanout`
- `plan-stream-emit`
