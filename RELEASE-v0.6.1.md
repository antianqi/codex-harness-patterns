# v0.6.1 — Trigger descriptions rewritten for LLM matching

Patch release focused on a single quality issue: the 18 Skills' frontmatter `description`
fields were too abstract for reliable LLM matching. The LLM could see the descriptions in
its system prompt, but the keywords in the descriptions were vague ("when planning
complex work", "when a tool fails"). The LLM would miss obvious triggers.

## What's in this release

**All 18 Skill descriptions rewritten** to a structured 4-line format:

```yaml
description: |
  <one-sentence purpose>.
  USE WHEN: <comma-separated concrete signals and keywords>.
  TRIGGER PHRASES: <user-original-language phrases the user might say>.
  SKIP WHEN: <anti-patterns where this skill does not apply>.
```

Example for `error-recovery-strategy`:

```yaml
description: |
  Classify error into 4 buckets (transient / deterministic / stale / unknown) and pick one of 5 actions (retry / switch / fallback / refresh-then-retry / ask-user / skip).
  USE WHEN: tool returns non-success, sub-agent `status: closed-failed`, exception escapes, timeout fires, weird partial-success result, ECONNREFUSED / 5xx / 429 / timeout / permission denied / "command not found" / "fail" / "error" / "出错了" / "挂" / "失败".
  TRIGGER PHRASES: "出错了", "failed", "挂", "error", "失败", "fail", "permission denied", "command not found", "ECONNREFUSED", "timeout", "挂了", "再试一次", "retry", "这不行", "没用", "fallback", "退路", "不行", "跑不通", "broken".
  SKIP WHEN: operation succeeded, error is in user input (clarification case), error is part of expected flow (grep 0 matches).
```

The LLM can now:
1. Grep keywords (ECONNREFUSED, permission denied, etc.) — exact match
2. Match user phrases ("出错了", "retry", "permission denied") — natural language
3. Know when NOT to apply (the SKIP WHEN section) — fewer false positives

## Why this matters

The user asked: "Can you actually remember to use these skills, or do you need prompt-based
triggers?" The honest answer was: I cannot remember reliably, the descriptions were too
abstract to match concrete situations, and meta-skills don't fix the meta-problem.

The real fix is **better descriptions** that the LLM can match on real signals. This release
is that fix: every Skill's description now reads like a search query, not a paragraph of
prose.

## Versions

- Manifest: `0.6.0` → `0.6.1` (patch bump: frontmatter-only change)
- All Skill versions bumped to `0.1.1` (or `1.0.1` for the v1.0 skills)

## No behavioral changes

The Skills' process, output contract, examples, and verification checklists are unchanged.
Only the frontmatter `description` field was rewritten. This is a documentation /
discoverability change, not a behavior change.

## Full Skill set (v0.6.1, 18 Skills — unchanged from v0.6.0)

| # | Skill | Added in |
|---|---|---|
| 1 | `tool-output-budget` | v0.1.0 |
| 2 | `context-pressure-compact` | v0.1.0 → v1.0 (v0.5.0) |
| 3 | `parallel-fanout` | v0.1.0 → v1.0 (v0.4.0) |
| 4 | `plan-stream-emit` | v0.1.0 |
| 5 | `review-mode` | v0.2.0 |
| 6 | `delegate-with-context` | v0.2.0 → v1.0 (v0.5.0) |
| 7 | `world-state-tracking` | v0.2.0 |
| 8 | `background-task` | v0.2.0 |
| 9 | `goal-persistence` | v0.3.0 → v1.0 (v0.4.0) |
| 10 | `model-router` | v0.3.0 |
| 11 | `completion-audit` | v0.4.0 |
| 12 | `fork-context-decision` | v0.4.0 |
| 13 | `subagent-family-tracking` | v0.5.0 |
| 14 | `goal-token-budgeting` | v0.5.0 |
| 15 | `error-recovery-strategy` | v0.6.0 |
| 16 | `retry-with-backoff` | v0.6.0 |
| 17 | `streaming-output-reader` | v0.6.0 |
| 18 | `session-handoff` | v0.6.0 |

## How to install

**From the official registry (recommended):**

This Plugin is also published in
[`MiniMax-AI/MiniMax-Code-Plugins`](https://github.com/MiniMax-AI/MiniMax-Code-Plugins) under
`plugins/antianqi/codex-harness-patterns`. Once PR
[#18](https://github.com/MiniMax-AI/MiniMax-Code-Plugins/pull/18) is merged, you can install
it from MiniMax Code's `/plugins` UI.

**From this standalone repo:**

```bash
git clone https://github.com/antianqi/codex-harness-patterns.git
cd codex-harness-patterns
git checkout v0.6.1
# copy skills/ into your MiniMax-Code-Plugins fork under
# plugins/<your-github-username>/codex-harness-patterns/skills/
```

## Validation

`npm run check` passes for this Plugin in the official registry's fork.

## License

Apache-2.0

## Related

- Official PR: <https://github.com/MiniMax-AI/MiniMax-Code-Plugins/pull/18>
- Upstream fork (PR source): <https://github.com/antianqi/MiniMax-Code-Plugins-1>
- v0.6.0 release: <https://github.com/antianqi/codex-harness-patterns/releases/tag/v0.6.0>
- Plugin source analysis: <https://github.com/openai/codex> (Apache-2.0)
