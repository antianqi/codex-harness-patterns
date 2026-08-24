# Changelog

## v0.6.2 (2026-08-24) — patch

**诚实记录型 patch**:复盘发现 Plugin 实际只覆盖了 Codex 模式库的 ~60%,并启动 2-3 月系统性补完计划。

### Changed

- `plugin.json`:version `0.6.1` → `0.6.2`
- CATALOG §7 修正:`P-49 Fork` / `P-50 Rollback` / `P-51 Recover` / `P-52 History Mode` 从 ⛔ 改 🟡
- CATALOG §8 修正:`P-63 Skills runtime` / `P-64 Memory system` 从 ❌ 改 🟡
- CATALOG §9 新增:~100 个未研究模式草案
- `RESEARCH-ROADMAP.md` 新建:2-3 月补完计划
- 6 篇纠错笔记新增:`knowledge/P-{49,50,51,52,63,64}-*.md`

### Not changed

- 18 skill 主体(版本号全部不变)
- 18 skill frontmatter
- 18 skill 的输出契约 / 验证清单

### Next

- v0.7.0:周 1-4 深读 5 大核心 crate
- v1.0.0:阶段 4 — 5 个新 skill + Plugin 大版本

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
