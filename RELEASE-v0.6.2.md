# v0.6.2 — 2026-08-24

## 概览

诚实记录型 patch。复盘发现 Plugin 实际只覆盖了 Codex 模式库的 ~60%,并启动 2-3 月系统性补完计划。

## 变更详情

### 元数据

- `plugin.json` version: `0.6.1` → `0.6.2`(patch bump,manifest 变更)
- 18 skill 全部不变(版本号 / frontmatter / 行为契约)

### CATALOG 修正(诚实记录)

| 模式 | 之前 | 修正后 | 原因 |
|---|---|---|---|
| P-49 Fork | ⛔ 范围外 | 🟡 待深读 | 实际是 `thread-store/paginated_fork.rs` 完整实现 |
| P-50 Rollback | ⛔ 范围外 | 🟡 待深读 | 实际是 `thread-store/revert_thread.rs` + `Op::ThreadRollback` |
| P-51 Recover | ⛔ 范围外 | 🟡 待深读 | 实际是 `Op::RecoverTurn` + `turn_suspension.rs` |
| P-52 History Mode | ⛔ 范围外 | 🟡 待深读 | 实际是 `ThreadHistoryMode` + `thread_history/*` |
| P-63 Skills | ❌ 不在 4 重点 | 🟡 待深读 | 实际是 Plugin 模仿对象 |
| P-64 Memory | ❌ 不在 4 重点 | 🟡 待深读 | 实际是跨 session 长期记忆系统 |

### 新增文档

- `RESEARCH-ROADMAP.md`(12KB)— 2-3 月系统性补完计划,分阶段 0-4
- `research-log/2026-08-24-resurvey-findings.md`(25KB)— 完整复盘报告
- 6 篇纠错笔记(`knowledge/P-{49,50,51,52,63,64}-*.md`)

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` 推送成功(commit `4a7b838`)
- PR #18 已自动更新(`MiniMax-AI/MiniMax-Code-Plugins/pull/18`)

## 下一步

- v0.7.0 minor:周 1-4 深读 5 大核心 crate(memories / skills / thread-store / core-plugins / prompts)
- v0.8.0 minor:周 5-8 次重要 crate
- v0.9.0 minor:周 9-10 边角 crate 收口
- v1.0.0 major:阶段 4 — 5 个新 skill + Plugin 大版本
