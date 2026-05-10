---
title: stitch2
created: 2026-05-10
updated: 2026-05-10
type: entity
tags: [ai-tool, design-tool, agent, open-source]
sources: [raw/articles/2026-05-05-stitch2-AI设计.md]
---

# Stitch 2.0

Google Labs 的 AI UI 设计工具，前身为 Galileo AI（2025 年 Google I/O 收购后更名）。2026 年 3 月 18 日发布 2.0 重大更新。被视为 Figma 的强力竞品（更新后 Figma 股价两日累跌 11%）。

**官网：** stitch.withgoogle.com | **定价：** 完全免费

## 8 大核心功能

1. **Vibe Design（氛围设计）** — 从「用户感受到什么」出发，非从线框图出发
2. **Voice Canvas（语音画布）** — 语音实时交互设计
3. **Design Agent** — 追踪项目历史，跨版本推理
4. **Agent Manager** — 并行探索多个设计方向
5. **AI 原生无限画布** — 支持 URL 提取设计系统、直接编辑
6. **即时原型** — 多屏连接 + 自动生成后续屏
7. **图片转 UI** — 草图 → 高保真
8. **全局主题管理** — Material Design 3 设计令牌深度集成

## 模型

| 模型 | 定位 | 配额 |
|------|------|------|
| Gemini 2.5 Flash | 标准 | 350 次/月 |
| Gemini 2.5 Pro | 实验 | 50 次/月 |
| Gemini 3 | 最新 (2025.12) | — |

## 与 Wiki 生态的关系

- **[[暗壳ai]]** — 同为 AI 设计工具，架构高度相似（Agent + 画布 + Skills），见 [[stitch2-vs-暗壳ai]] 对比页面
- **[[cursor-debug]] / [[windsurf-codemaps]]** — Stitch 的 MCP 服务器支持 Cursor、Claude Code，导出代码后交给编码助手完成业务逻辑
- **[[hermes-agentic-workflows]]** — Design Agent + Agent Manager 是多 agent 协同实例，与 Hermes subagent 编排理念相通
- **[[browser-harness]]** — 可导出 web 前端代码，形成「设计 → 实现 → 测试」流水线

## 更多

- **DESIGN.md** — 跨平台设计规则同步
- **Antigravity IDE** — 集成开发环境
- 推荐工作流：30 分钟出完整 Landing Page（独立开发者友好）