# Changelog

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

Manifest bumped to `0.2.0`. Total Skills: 8.

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
