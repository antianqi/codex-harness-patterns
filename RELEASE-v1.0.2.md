# v1.0.2 — 2026-08-25

## 概览

按 mcode plugin 提交规范的合规 patch。

## 变更

- README 新增 `Disclosure (per mcode plugin convention)` 一节,4 段独立披露:
  - **No credentials** — 不读 / 存 / 传 / 请求任何凭据
  - **No network** — 任何出站调用 / socket / 自动更新
  - **No telemetry** — 任何自身指标 / trace / event / log
  - **No third-party services** — 不绑 MCP / npm / 原生 binary / 外部 runtime
- PR #18 body 改为 `Design compliance / Validation / Test evidence` 三段式
- 跨平台 path 验证:无硬编码 `C:\` / `D:\` / `/Users/` / `/home/`

## 未变更

- 23 skills 主体(版本号不变)
- 23 skills frontmatter
- plugin.json 其他字段
- License

## 验证

- fork `antianqi/MiniMax-Code-Plugins-1` commit `5b7f1a8` 推送成功
- PR #18 body 同步更新

## 下一步

- 等 PR #18 review
- 装 v1.0.2 到 mcode 跑真实任务,收集 skill 选中数据
