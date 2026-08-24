# v0.7.2 — 2026-08-25

## 概览

研究里程碑型 patch。阶段 2 周 6 完成 — `codex-rs/tools/` 25+ 文件深读,**Tool 运行时全栈**。

## 变更详情

### 元数据

- `plugin.json` version: `0.7.1` → `0.7.2`(patch bump)
- 18 skill 全部不变

### 新增知识笔记(4 篇)

| 文件 | 大小 | 覆盖模式 |
|---|---|---|
| `knowledge/P-107-108-tool-discovery-search.md` | 5KB | Discovery 二维分类 + search defer_loading |
| `knowledge/P-109-111-dynamic-mcp-tool.md` | 6KB | Dynamic 简单 vs MCP 复杂适配器 |
| `knowledge/P-112-113-plugin-install-responses-api.md` | 5KB | Tool suggestion 审批 + Responses API 5 类型 |
| `knowledge/P-114-116-json-schema-image-response-history.md` | 5KB | JSON Schema 子集 + 稳定输出 |

### CATALOG 状态变更

| ID | 之前 | 现在 |
|---|---|---|
| P-107 Tool discovery | 🟡 | 🟢 |
| P-108 Tool search | 🟡 | 🟢 |
| P-109 Dynamic tool protocol | 🟡 | 🟢 |
| P-110 Dynamic tool runtime | 🟡 | 🟢 |
| P-111 MCP tool runtime | 🟡 | 🟢 |
| P-112 Plugin install request | 🟡 | 🟢 |
| P-113 Responses API tool | 🟡 | 🟢 |
| P-114 JSON Schema policy | 🟡 | 🟢 |

**🟢 首次突破 100 个已掌握模式**

### 关键洞察

**Tool 运行时全栈**:
```
Discovery (P-107)    →  Search (P-108)    →  Loading (defer)
                                            ↓
                  Dynamic (P-109/110)  |  MCP (P-111)
                                            ↓
                Plugin Install (P-112) | Responses API (P-113)
                                            ↓
                            JSON Schema (P-114) — 协议层
```

**Plugin 借鉴模式**:
- "简单 vs 复杂适配器" — Plugin manifest 简单,内部容错复杂
- "defer loading" — Skill description 简洁(关键词匹配)
- "OpenAI 协议补全" — 跟 3rd-party 兼容
- "Tool suggestion 审批" — 任何"加新能力"都该走审批

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` 推送成功(commit `2d8fed0`)
- PR #18 已自动更新

## 下一步

- v0.7.3:周 7 — `codex-rs/rollout/` + `codex-rs/models-manager/`
- v0.7.4:周 8 — `codex-rs/protocol/src/` 完整
- v0.8.0:阶段 2 整圈收口
