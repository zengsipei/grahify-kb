---
title: Graphify
created: 2026-05-08
updated: 2026-05-08
type: entity
tags: [tool, knowledge-graph, visualization, code-indexing, llm-wiki]
sources: [raw/articles/2026-05-05-graphify.md]
confidence: high
---

# Graphify

**Graphify** 是 Karpathy LLM Wiki 理念的产品化实现 —— 一个给人看的双链知识图谱工具。

## 概述

- **定位**: 知识图谱 + 可视化（给人看）
- **语言**: Python 3.10+
- **安装**: `pip install graphifyy`（注意包名是 graphifyy，CLI 命令是 graphify）
- **许可证**: MIT

## 核心能力

| 功能 | 说明 |
|------|------|
| Tree-sitter 静态分析 | 28+ 编程语言的 AST 解析 |
| LLM 语义提取 | 代码、文档、PDF、图片的多模态理解 |
| 知识图谱 | NetworkX 图结构，支持查询 |
| 交互可视化 | D3.js force-directed graph.html |
| 社区检测 | Leiden 算法（无向量） |
| Token 压缩 | 71.5× 压缩比 |

## 输出结构

```
graphify-out/
├── graph.html        # 交互式可视化
├── GRAPH_REPORT.md   # 核心节点、惊喜发现、建议问题
├── graph.json        # 可查询的持久化图谱
└── cache/            # 增量缓存
```

## 与 GitNexus 的区别

| 维度 | Graphify | GitNexus |
|------|----------|----------|
| 定位 | 知识图谱 + 可视化 | 代码索引 + MCP 工具 |
| 输出 | graph.html | MCP 工具调用 |
| 输入 | 代码 + 论文 + 文档 + 图片 | 代码仓库 |
| 语言 | Python | Node.js |

## 与 Wiki 的集成

Graphify 与 llm-wiki 互补：
- **Wiki**: 手动维护的双链 markdown，交叉引用精确
- **Graphify**: 自动从代码/文档生成语义图谱，发现隐藏联系

Wiki 可用 Graphify 来增强发现能力：`graphify update .`

## 相关页面

- [[hermes-agentic-workflows]] — Hermes 的 delegate_task 可与 Graphify 配合
- [[cursor-debug]] — 调试技巧（Graphify 可帮助理解代码关系）
- [[supabase-vs-firebase]] — 数据库对比（Graphify vs GitNexus 类似的维度对比思路）