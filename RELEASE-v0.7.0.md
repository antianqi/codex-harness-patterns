# v0.7.0 — 2026-08-24

## 概览

**Plugin 里程碑 minor 版本**。阶段 1(5 大核心 crate)整圈收口。

## 阶段 1 整圈回顾

| 周 | crate | 状态 | 发布 |
|---|---|---|---|
| 1 | `codex-rs/memories/` 21 文件 | ✅ | v0.6.3 |
| 2 | `codex-rs/skills/` 10+ 文件 | ✅ | v0.6.4 |
| 3 | `codex-rs/thread-store/` 40+ 文件 | ✅ | v0.6.5 |
| 4 | `codex-rs/core-plugins/` 60+ 文件 + `codex-rs/prompts/` 4 套 | ✅ | **v0.7.0** |

**5 大核心 crate 全部完成**:
- ✅ memories(跨 session 长期记忆)
- ✅ skills(Plugin 直接对应物)
- ✅ thread-store(完整 session 持久化)
- ✅ core-plugins(Plugin 运行时)
- ✅ prompts(4 套 prompt 模板)

## 变更详情

### 元数据

- `plugin.json` version: `0.6.5` → `0.7.0`(**minor bump**)
- 18 skill 全部不变(只增知识,不增 skill)

### 新增知识笔记(5 篇)

| 文件 | 大小 | 覆盖模式 |
|---|---|---|
| `knowledge/P-93-95-plugin-loader-marketplace-manifest.md` | 7KB | P-93/94/95 Plugin 运行时 + marketplace + manifest |
| `knowledge/P-99-plugin-startup-sync.md` | 4KB | P-99 3 层 fallback + lock + SHA 缓存 |
| `knowledge/P-164-prompts-compact.md` | 3KB | P-164 compact 5 个 must-have |
| `knowledge/P-165-prompts-goals.md` | 5KB | P-165 4 大设计原则 |
| `knowledge/P-166-168-prompts-permissions-realtime-review.md` | 8KB | P-166/167/168 8+3+3 套 prompt |

### CATALOG 状态变更

| ID | 之前 | 现在 |
|---|---|---|
| P-93 Plugin manager/loader | 🟡 | 🟢 |
| P-94 Plugin marketplace | 🟡 | 🟢 |
| P-95 Plugin manifest | 🟡 | 🟢 |
| P-99 Plugin startup sync | 🟡 | 🟢 |
| P-164 Prompts compact | 🟡 | 🟢 |
| P-165 Prompts goals | 🟡 | 🟢 |
| P-166 Prompts permissions | 🟡 | 🟢 |
| P-167 Prompts realtime | 🟡 | 🟢 |
| P-168 Prompts review | 🟡 | 🟢 |

### Plugin 覆盖率

- **v0.6.2(开始)**:60%
- **v0.6.3(周 1)**:62% → 64%
- **v0.6.4(周 2)**:64% → 66%
- **v0.6.5(周 3)**:66% → 72%
- **v0.7.0(周 4)**:72% → **78%**

**阶段 1 净增**:**+18%**(60% → 78%)

## 关键洞察

1. **Codex skills 系统的 selection/loading/parser/mentions/model 是我们 Plugin 的直接对应物** —— Plugin 的"skill 选取"能力**远弱于** Codex,这是新 skill `skill-auto-select` 的来源。
2. **thread-store 提供完整 session 持久化层** —— Lineage + Migration + ModelContext reconstruction 三件套是新 skill `session-branch-fork` 的核心参考。
3. **Prompts 系统是结构化的** —— `include_str!` 编译时打包 + 模板变量 + 强约束的 must-have 列表,我们的 Skill 是 markdown 文档,弱约束。
4. **Plugin manifest 多 ecosystem 兼容** —— 支持 OpenAI / Claude / Cursor 三家,我们的 plugin.json 只支持 .codex-plugin。
5. **Startup sync 三层 fallback** —— GitHub API → Backend archive → Git clone,任何外网同步都该有这模式。

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` 推送成功(commit `ab97ec7`)
- PR #18 已自动更新

## 下一步

- 阶段 2(周 5-8):core/agent/ + core/session/ + tools/ + rollout/ + models-manager/ + protocol/
- 阶段 3(周 9-10):边角 crate 收口
- 阶段 4(周 11-12):5 个新 skill + Plugin v1.0
