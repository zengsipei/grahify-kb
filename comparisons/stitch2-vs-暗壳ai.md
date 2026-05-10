---
title: stitch2-vs-暗壳ai
created: 2026-05-10
updated: 2026-05-10
type: comparison
tags: [comparison, design-tool, agent]
sources: [raw/articles/2026-05-05-stitch2-AI设计.md, raw/articles/2026-05-05-暗壳AI室内设计.md]
---

# Stitch 2.0 vs 暗壳AI

AI 设计工具的两条路线：通用 UI 设计（Google Stitch）vs 垂直室内设计（暗壳AI）。

## 对比

| 维度 | Stitch 2.0 | 暗壳AI |
|------|------------|--------|
| **领域** | 通用 UI / Web 设计 | 垂直室内设计 |
| **开发商** | Google Labs（原 Galileo AI） | 暗壳科技（ark.art） |
| **发布** | 2026.03.18（2.0） | 2024 上线，2026.03.31（Agent 2.0） |
| **核心 Agent** | Design Agent（追踪项目历史） | AI Agent 2.0（空间智能设计） |
| **技能体系** | — | Skills 技能库（100+ 垂直技能，10000+ 设计师） |
| **交互** | Vibe Design + Voice Canvas | 协同自由画布 |
| **生态** | Material Design 3 令牌 | 100+ 品牌、30 万+ SKU |
| **多 Agent** | Agent Manager（并行） | 多智能体协作体系 |
| **定价** | 完全免费 | — |
| **代码导出** | MCP 导出 → Cursor/Claude Code | 无直接编码关联 |
| **独特功能** | 语音画布、图片转 UI | 一键抠图、高清放大、材质替换 |

## 共同架构模式

两者共享「AI Agent + 协同画布 + Skills 技能库」三层架构，是 AI 设计工具的主流范式：

- **Agent 层**：理解模糊需求、自主推理
- **画布层**：可视化协作界面
- **技能层**：可复用设计能力

这与 [[hermes-agentic-workflows]] 中的 subagent 编排理念有共通之处（多 agent 协同分工）。

## 相关页面

- [[stitch2]] — Stitch 2.0 详情
- [[暗壳ai]] — 暗壳AI 详情
- [[hermes-agentic-workflows]] — Agent 编排模式
- [[codex-cli-goal]] — Agent 目标管理（设计 Agent 的目标持久化对比）