# v0.6.5 — 2026-08-24

## 概览

研究里程碑型 patch。阶段 1 周 3 完成 — `codex-rs/thread-store/` 40+ 文件深读,**完整 session 持久化层**。

## 变更详情

### 元数据

- `plugin.json` version: `0.6.4` → `0.6.5`(patch bump)
- 18 skill 全部不变

### 新增知识笔记(6 篇)

| 文件 | 大小 | 覆盖模式 |
|---|---|---|
| `knowledge/P-67-thread-sections.md` | 4KB | Thread sections + operation-tagged state access |
| `knowledge/P-68-thread-projects.md` | 4KB | Thread projects + 三态更新 + idempotency key |
| `knowledge/P-69-70-queue-search.md` | 5KB | Queue change-based polling + Search snippet |
| `knowledge/P-71-72-migration-lineage.md` | 6KB | Rollout migration + bounded subagent replay |
| `knowledge/P-76-model-context-reconstruction.md` | 4KB | ReverseJsonlScanner + bounded replay |
| `knowledge/P-77-thread-history-segmentation.md` | 5KB | 跨 segment 双向 cursor |

### CATALOG 状态变更

| ID | 之前 | 现在 |
|---|---|---|
| P-67 Thread sections | 🟡 | 🟢 |
| P-68 Thread projects | 🟡 | 🟢 |
| P-69 Thread queue | 🟡 | 🟢 |
| P-70 Thread search | 🟡 | 🟢 |
| P-71 Rollout migration | 🟡 | 🟢 |
| P-72 Rollout + subagent lineage | 🟡 | 🟢 |
| P-76 ModelContext reconstruction | 🟡 | 🟢 |
| P-77 Thread history segmentation | 🟡 | 🟢 |

**🟡 首次清零** — 所有 🟡 模式都进入 🟢

### 关键洞察

`thread-store/` 提供**两层**能力:
- **管理面**:Sections / Projects / Queue / Search
- **历史面**:Lineage / Migration / ModelContext reconstruction
- **抽象层**:`ThreadStore` trait + `LocalThreadStore` + `InMemoryThreadStore`

新 skill `session-branch-fork`(阶段 4)的核心参考全部在这里。

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` 推送成功(commit `cfadb53`)
- PR #18 已自动更新

## 下一步

- v0.6.6:周 4 — `codex-rs/core-plugins/` + `codex-rs/prompts/`(Plugin 运行时 + 4 套 prompt 模板)
- v0.7.0:阶段 1 整圈完成
