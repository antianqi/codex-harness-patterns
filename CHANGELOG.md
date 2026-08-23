# Changelog

## v0.4.0 (2026-08-24)

Added two Skills extracted from the Codex continuation template and the
V2 multi-agent protocol:

- `completion-audit` — before declaring a non-trivial task done, derive
  requirements, identify authoritative evidence for each, verify against
  the actual current state, and only declare done when every requirement
  has its own ✅. Mirrors the completion-audit section of the Codex goal
  continuation template (`ext/goal/templates/goals/continuation.md`).
- `fork-context-decision` — pick `all` / `N` / `none` for `fork_turns`
  explicitly, not by default. Mirrors the `fork_turns` semantics in
  Codex's V2 multi-agent protocol (`core/src/session/multi_agents.rs`).

Updated two Skills to v1.0 based on deeper reads of the Codex source:

- `goal-persistence` v1.0 — incorporated the completion-audit and
  blocked-audit sections from the Codex continuation template. Added the
  token-budget reporting rule. Aligned language with the canonical
  "treat completion as unproven" principle.
- `parallel-fanout` v1.0 — added the explicit-spawn principle (P-20:
  spawn is opt-in, not auto). Added `max_concurrency` awareness.
  Cross-referenced `fork-context-decision` and `delegate-with-context`.
  Added `completion-audit` on the aggregation before declaring done.

Total Skills: 12 (10 v1.0 + 2 new).

## v0.3.0 (2026-08-24)

Added two Skills that close the long-running task loop:

- `goal-persistence` — maintain an explicit north-star goal for the whole
  thread that survives compactions and detects drift. Mirrors
  `Op::SetThreadMemoryMode` + `EventMsg::ThreadGoalUpdated` in
  `codex-rs/protocol/src/protocol.rs`.
- `model-router` — before delegating a sub-task, classify the work into
  cheap / medium / main and pick the matching `model_config_id`. Mirrors
  `codex-rs/model-provider-info/` + `codex-rs/models-manager/`.

Total Skills: 10.

## v0.2.0 (2026-08-24)

Added four Skills that round out the long-running task toolkit:

- `review-mode` — switch to critic mode after finishing a chunk, produce a
  PASS / FIX / REDO verdict. Mirrors `EnteredReviewMode` /
  `ExitedReviewMode` in `codex-rs/protocol/src/protocol.rs`.
- `delegate-with-context` — write a minimal-context brief for `task()`
  instead of forwarding the full conversation history. Mirrors
  `InterAgentCommunication` / `CollabAgentSpawnBegin`.
- `world-state-tracking` — persist a structured state file that survives
  context compaction. Mirrors `WorldState` in
  `codex-rs/core/src/context/world_state.rs`.
- `background-task` — run long-running commands in the background with a
  log file, poll on later turns. Mirrors `unified_exec` /
  `CleanBackgroundTerminals`.

Total Skills: 8.

## v0.1.0 (2026-08-24) — initial release

Four Skills covering the highest-ROI patterns from OpenAI Codex harness v0.149.0:

- `tool-output-budget` — token-aware head+tail+marker truncation of
  oversized tool output. Mirrors `codex-rs/utils/output-truncation/`.
- `context-pressure-compact` — structured snapshot before continuing a
  long task. Mirrors `codex-rs/core/src/compact.rs::run_pre_sampling_compact`.
- `parallel-fanout` — dispatch 2+ independent sub-tasks with `task` and
  aggregate. Mirrors `FuturesUnordered` in
  `codex-rs/core/src/thread_manager.rs`.
- `plan-stream-emit` — emit a `todowrite`-shaped plan before non-trivial
  work. Mirrors `PlanUpdate` / `PlanDelta` events in
  `codex-rs/protocol/src/protocol.rs`.
