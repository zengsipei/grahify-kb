---
title: gitnexus
created: 2026-05-10
updated: 2026-05-10
type: entity
tags: [ai-tool, code-indexing, knowledge-graph, mcp, open-source]
sources: [raw/articles/2026-05-05-gitnexus.md]
---

# GitNexus

零服务器代码智能引擎。将代码库索引为知识图谱，通过 MCP 或 CLI 暴露给 AI agent，让 agent 改代码时能追踪依赖链、调用链和影响范围。

**类型：** npm 包（`npx gitnexus`），GitHub: [abhigyanpatwari/GitNexus](https://github.com/abhigyanpatwari/GitNexus)

## 两种使用模式

| 模式 | 方式 | 特点 |
|------|------|------|
| CLI + MCP | 命令行索引 + MCP 服务器 | 推荐，可集成到 Claude Code / Cursor / Codex 等 agent |
| Web UI | `gitnexus serve` | 含可视化图谱 + AI 聊天 |

## 核心功能

- **analyze** — 索引代码仓库（支持 14 种编程语言），可选 `--skills` 生成仓库技能文件
- **mcp** — 启动 MCP 服务器，暴露 16 个 MCP 工具给 agent
- **serve** — 启动 Web UI（可视化 + 聊天）
- **wiki** — 从图谱自动生成 wiki 文档
- **group** — 多仓库跨仓库合约匹配

### MCP 工具亮点

- 混合搜索（BM25 + 语义 + RRF）
- 360° 符号视图
- 爆炸半径影响分析
- Git diff 影响映射
- 多文件协调重命名
- 原始 Cypher 查询

## 与 Wiki 生态的关系

- **[[graphify]]** — 同为代码→知识图谱工具。GitNexus 侧重 Agent 运行时检索（MCP），graphify 侧重静态分析+可视化，互补关系
- **[[windsurf-codemaps]]** — GitNexus 支持的编码助手之一（codemaps 提供代码地图，GitNexus 提供依赖链）
- **[[cursor-debug]]** — 同样支持 Cursor IDE 集成
- **[[hermes-agentic-workflows]]** — MCP 集成与 Hermes subagent 编排理念相通。GitNexus 的 `--skills` 生成机制与 Hermes skill 体系呼应
- **[[browser-harness]]** — 都通过 MCP 暴露能力给 agent