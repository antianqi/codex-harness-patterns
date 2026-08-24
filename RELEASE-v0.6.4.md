# v0.6.4 — 2026-08-24

## 概览

研究里程碑型 patch。阶段 1 周 2 完成 — `codex-rs/skills/` 10+ 文件深读,**Plugin 直接对应物**。

## 变更详情

### 元数据

- `plugin.json` version: `0.6.3` → `0.6.4`(patch bump)
- 18 skill 全部不变

### 新增知识笔记(6 篇)

| 文件 | 大小 | 覆盖模式 |
|---|---|---|
| `knowledge/P-85-skill-selection-algorithm.md` | 6KB | Skill 选取算法 + 三层匹配 |
| `knowledge/P-86-skill-loading.md` | 6KB | 加载抽象 + 缓存 + system skills |
| `knowledge/P-87-skill-frontmatter-parser.md` | 6KB | Frontmatter 解析 + 容错 |
| `knowledge/P-88-skill-mention-extractor.md` | 5KB | `$skill-name` 语法 |
| `knowledge/P-89-implicit-skill-invocation.md` | 5KB | Shell 隐式调用 + 平台感知 |
| `knowledge/P-92-skill-metadata-model.md` | 6KB | 11 字段 metadata + 双形态 |

### CATALOG 状态变更

| ID | 之前 | 现在 |
|---|---|---|
| P-85 Skill selection | 🟡 | 🟢 |
| P-86 Skill loading | 🟡 | 🟢 |
| P-87 Frontmatter parser | 🟡 | 🟢 |
| P-88 Mention extractor | 🟡 | 🟢 |
| P-89 Implicit invocation | 🟡 | 🟢 |
| P-92 Metadata model | 🟡 | 🟢 |

### 关键洞察

**Plugin 当前实现的差距**:
| 维度 | Codex skills/ | 我们的 Plugin |
|---|---|---|
| 显式 + 隐式 selection | ✓ | ❌ |
| 三层匹配 | ✓ | ❌ |
| `$name` 语法 | ✓ | ❌ |
| Frontmatter 解析 | ✓ | ❌ |
| 系统 skill 嵌入式分发 | ✓ | ❌ |
| 名字冲突检测 | ✓ | ❌ |

Plugin 的"skill 选取"能力**远弱于** Codex skills/ — 这是新 skill `skill-auto-select` 的来源(阶段 4 计划)。

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` 推送成功(commit `3616b16`)
- PR #18 已自动更新

## 下一步

- v0.6.5:周 3 — `codex-rs/thread-store/` 40+ 文件深读(P-49/50/51/52 完整实现 + 8 个新增模式)
- v0.7.0:周 4 — `codex-rs/core-plugins/` + `prompts/`
