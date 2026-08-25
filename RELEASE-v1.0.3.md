# v1.0.3 — 2026-08-25

## 概览

响应 PR #18 hetaoBackend 给的 CHANGES_REQUESTED review(2026-08-25),3 个 blocking issue 全部修复。

## Reviewer issues(PR #18 review)

1. **文档版本不一致** — PR-STATUS.md / README / OVERVIEW 跟 v1.0.x manifest 不同步
2. **Codex-only 工具参数** — 5 个 SKILL.md 用了 mcode 不存在的 Codex 参数
3. **plugin-authoring / memory 写行为未声明 host 边界** — 2 个 SKILL.md 描述副作用但未要求 user 确认

## 修复(2 个 commit)

### commit 1 · 5 SKILL.md 移除 Codex-only 参数
- `fork-context-decision`(0.1.1 → 0.1.2)
- `parallel-fanout`(1.0.1 → 1.0.2)
- `delegate-with-context`(1.0.1 → 1.0.2)
- `background-task`(0.1.1 → 0.1.2)
- `model-router`(0.1.1 → 0.3.2)

example 改为 pseudocode + "mcode 适配" 注释,教设计决策不教参数拼写。

### commit 2 · 2 SKILL.md 加 Host runtime requirements 段
- `plugin-author-helper`
- `long-term-memory`

声明所有副作用(网络 / 文件写 / 子 agent / 调度触发)需 user 确认才能执行。

## 未变更

- 18 个未涉及 SKILL.md
- plugin.json / License
- README 4-section disclosure(已在 v1.0.2 完成)

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` 已推送 commits `1f4530c` + `6f1a615`
- 7 个 SKILL.md 改动已通过 `core.autocrlf = false` 的本地 commit round-trip
- PR #18 review 仍显示 `CHANGES_REQUESTED`,但所有 issue 已 address,等 reviewer 复核

## 下一步

- 等 hetaoBackend 重新 review
- 装 v1.0.3 到 mcode 跑真实任务,验证 7 个 SKILL.md 改完后 LLM 实际行为符合预期
