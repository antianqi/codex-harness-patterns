# Changelog

## v0.6.1 (2026-08-24)

**Trigger descriptions rewritten across all 18 Skills** for better LLM matching.

Each `description:` frontmatter field now uses a structured 4-line format:

```yaml
description: |
  <one-sentence purpose>.
  USE WHEN: <comma-separated concrete signals and keywords>.
  TRIGGER PHRASES: <user-original-language phrases the user might say>.
  SKIP WHEN: <anti-patterns where this skill does not apply>.
```

This makes the description **keyword-greppable** (so the LLM can match on real signals
like "ECONNREFUSED", "permission denied", "retries exceeded", "上下文满了" / "出错了" /
"重试") instead of trying to interpret abstract prose.

All 18 Skills have their trigger phrases now spelled out in both English and Chinese, so
the LLM can match user language directly. Skill versions bumped to `0.1.1` (or
`1.0.1` for the v1.0 skills). Manifest bumped to `0.6.1` (patch bump for frontmatter
fixes).

No new Skills, no behavioral changes — just better trigger descriptions so the LLM
actually uses the Skills at the right time.

## v0.6.0 (2026-08-24)

Added four Skills:

- `error-recovery-strategy`
- `retry-with-backoff`
- `streaming-output-reader`
- `session-handoff`

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
