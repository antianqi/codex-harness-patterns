# Changelog

## v0.7.2 (2026-08-25) — patch (research milestone: Phase 2 Week 6)

阶段 2 周 6 完成 — `codex-rs/tools/` 25+ 文件深读。

### Added

- 4 篇新知识笔记:
  - `P-107-108-tool-discovery-search.md`(5KB)— Tool discovery + search
  - `P-109-111-dynamic-mcp-tool.md`(6KB)— Dynamic + MCP tool
  - `P-112-113-plugin-install-responses-api.md`(5KB)— Plugin install + Responses API
  - `P-114-116-json-schema-image-response-history.md`(5KB)— JSON Schema + image + response
- CATALOG 状态:🟢 92→100 / 🟡 5→3
- **🟢 首次突破 100 个已掌握模式**

## v0.7.1 (2026-08-25) — patch (research milestone: Phase 2 Week 5)

阶段 2 周 5 完成 — `codex-rs/core/src/agent/` + `core/session/` + `core/context_manager/` 关键未读模块。

### Added

- 4 篇新知识笔记:
  - `P-134-138-agent-registry.md`(7KB)— AgentRegistry + 角色覆盖
  - `P-140-142-context-manager.md`(5KB)— Arc<Vec> CoW + history_version
  - `P-158-turn-suspension.md`(6KB)— 完整 9 步 suspend 流程
  - `P-157-162-session-infrastructure.md`(5KB)— budget / MCP refresh / queue
- CATALOG 状态:🟢 82→92 / 🟡 1→5

## v0.7.0 (2026-08-24) — minor (research milestone: Phase 1 COMPLETE)

**Plugin 里程碑** — 阶段 1 整圈收口,5 大核心 crate 全部完成。

### Phase 1 整圈回顾

| 周 | crate | 状态 | 发布 |
|---|---|---|---|
| 1 | `codex-rs/memories/` 21 文件 | ✅ | v0.6.3 |
| 2 | `codex-rs/skills/` 10+ 文件 | ✅ | v0.6.4 |
| 3 | `codex-rs/thread-store/` 40+ 文件 | ✅ | v0.6.5 |
| 4 | `codex-rs/core-plugins/` 60+ 文件 + `codex-rs/prompts/` 4 套 | ✅ | **v0.7.0** |

### Added

- 5 篇新知识笔记(P-93/94/95/99 + P-164/165/166-168)
- **Plugin 覆盖率 72% → 78%**(阶段 1 净增 16%)
- CATALOG 状态:🟢 74→82 / 🟡 0→1

### Not changed

- 18 skill 主体 / frontmatter / 输出契约

## v0.6.5 (2026-08-24) — patch (research milestone)

阶段 1 周 3 完成 — `codex-rs/thread-store/` 40+ 文件深读,**完整 session 持久化层**。

### Added

- 6 篇新知识笔记(P-67/68/69-70/71-72/76/77),全 🟡→🟢
- **🟡 首次清零** — 所有 🟡 模式都进入 🟢
- 关键洞察:thread-store 提供管理面(sections/projects/queue/search) + 历史面(lineage/migration/modelContext)

## v0.6.4 (2026-08-24) — patch (research milestone)

阶段 1 周 2 完成 — `codex-rs/skills/` 10+ 文件深读,**Plugin 直接对应物**。

### Added

- 6 篇新知识笔记(P-85/86/87/88/89/92),全 🟡→🟢
- 关键洞察:Codex skills 系统的 selection/loading/parser/mentions/model 直接对应我们 Plugin 结构
- 新 skill `skill-auto-select` 来源确认(阶段 4 计划)

### Not changed

- 18 skill 主体 / frontmatter / 输出契约

## v0.6.3 (2026-08-24) — patch (research milestone)

阶段 1 周 1 完成 — `codex-rs/memories/` 21 文件深读,4 个新模式 🟢。

### Added

- 4 篇新知识笔记:
  - `P-78-memory-phase1.md`(6KB)— Memory Phase 1:per-rollout extraction
  - `P-79-memory-phase2.md`(8KB)— Memory Phase 2:global consolidation
  - `P-80-memory-citation.md`(4KB)— MemoryCitation 协议 + 解析
  - `P-84-memory-workspace-git.md`(8KB)— Memory workspace + git baseline
- CATALOG 状态:`P-78 / P-79 / P-80 / P-84` 全部 🟡→🟢
- CATALOG §9.2 状态列加上"状态"字段

### Not changed

- 18 skill 主体 / frontmatter / 输出契约
- Plugin 主合约 / 触发条件

### Roadmap progress

| 阶段 | 状态 | 覆盖率 |
|---|---|---|
| 0 · 错判修正 | ✅ | 60%→62% |
| 1 · 5 大核心 | 🟢 周 1 | 62%→64% |
| 1 · 周 2 skills/ | ⏳ 下一步 | — |

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
