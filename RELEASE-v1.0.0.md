# v1.0.0 — 2026-08-25 🎉

## 概览

**Plugin 1.0 里程碑** — 23 个 Skill 完整覆盖 agent 生命周期。

## 重大变更

### 5 个新 Skill

| # | Skill | 用途 | 灵感来源 |
|---|---|---|---|
| 19 | `long-term-memory` | 跨 session 长期记忆设计 | `codex-rs/memories/` |
| 20 | `skill-auto-select` | 设计可被 LLM 可靠选择的 skill | `codex-rs/skills/` |
| 21 | `plugin-author-helper` | 写 marketplace Plugin | `codex-rs/core-plugins/` |
| 22 | `tool-discovery-pattern` | 设计可被 agent 发现的 tool | `codex-rs/tools/` |
| 23 | `session-branch-fork` | session 分支 / 回滚 / 恢复 | `codex-rs/thread-store/` |

### 完整 agent 生命周期覆盖

```
planning → decomposition → sub-agent parallelism → execution →
state tracking → tool discovery → skill/plugin authoring →
memory persistence → session branching
```

## Plugin 覆盖率旅程

- **v0.6.2**(开始):60% — CATALOG 49/66 🟢
- **v0.7.0**(阶段 1):78% — 5 大核心 crate(memories / skills / thread-store / core-plugins / prompts)
- **v0.7.5**(阶段 3):88% — 次重要 crate + 边角 crate
- **v1.0.0**(阶段 4):**90%+** — 5 个新 Skill 收口

## 研究方法

3 个月的 4 阶段研究:
- **阶段 0**:6 个错判修正(8 月 24 日)
- **阶段 1**:5 大核心 crate(8 月 24-25 日,4 周)
- **阶段 2**:次重要 crate(core/agent/ + tools/ + rollout/ + models-manager/ + protocol/)(8 月 25 日,4 周)
- **阶段 3**:边角 crate 收口(apply-patch / context-fragments / mcp-server / app-server-daemon)(8 月 25 日,1 周)
- **阶段 4**:5 个新 Skill 落地(8 月 25 日,1 天)

## 完整 changelog

| 版本 | 类型 | 内容 | 日期 |
|---|---|---|---|
| v0.1.0 - v0.2.0 | minor | 4→8 skills 初始迭代 | 2026-08-24 |
| v0.3.0 | minor | +goal-persistence +model-router (10 skills) | 2026-08-24 |
| v0.4.0 | minor | +completion-audit +fork-context-decision (12 skills) | 2026-08-24 |
| v0.5.0 | minor | +subagent-family-tracking +goal-token-budgeting (14 skills) | 2026-08-24 |
| v0.6.0 | minor | +error-recovery +retry +streaming +handoff (18 skills) | 2026-08-24 |
| v0.6.1 | patch | frontmatter 关键词化(EN/中文) | 2026-08-24 |
| v0.6.2 | patch | 6 个错判修正 + 路线图 | 2026-08-24 |
| v0.6.3 | patch | 阶段 1 周 1 — memories/ | 2026-08-24 |
| v0.6.4 | patch | 阶段 1 周 2 — skills/ | 2026-08-25 |
| v0.6.5 | patch | 阶段 1 周 3 — thread-store/ | 2026-08-25 |
| v0.7.0 | **minor** | 阶段 1 周 4 — core-plugins/ + prompts/ | 2026-08-25 |
| v0.7.1 | patch | 阶段 2 周 5 — agent + session | 2026-08-25 |
| v0.7.2 | patch | 阶段 2 周 6 — tools/ | 2026-08-25 |
| v0.7.3 | patch | 阶段 2 周 7 — rollout + models-manager | 2026-08-25 |
| v0.7.4 | patch | 阶段 2 周 8 — protocol/ | 2026-08-25 |
| v0.7.5 | patch | 阶段 3 — 边角 crate | 2026-08-25 |
| **v1.0.0** | **MAJOR** | **阶段 4 — 5 个新 Skill(23 total)** | 2026-08-25 |

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` commit `e2ec486` 推送成功
- PR #18 已自动更新
- 23 skills 全部就位

## 下一步(v1.0 之后)

Plugin v1.0 标志着研究完成,进入"成熟期":
- 内部 beta 反馈循环
- 跟踪 Codex 后续 release
- 持续打磨 23 skills
- 等待 v2 重大需求出现
