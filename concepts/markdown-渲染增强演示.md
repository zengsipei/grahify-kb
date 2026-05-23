---
title: Markdown 渲染增强演示
created: 2026-05-23
updated: 2026-05-23
type: concept
tags: [visualization, knowledge-mgmt]
sources: [raw/articles/2026-05-23-markdown-渲染增强演示.md]
---

# Markdown 渲染增强演示

本页面梳理 Wiki 系统 Markdown 渲染器的增强功能，展示超越基础 Markdown 的渲染能力。这些增强是 [[markdown-进阶语法]] 的实践落地，也与 [[ai-agent-输出格式研究]] 中讨论的"富文本输出"问题密切相关——结构化、可视化的渲染能力直接影响知识库的可读性和信息密度。

## Callout 提示框

支持 GitHub 风格的 Callout 语法，通过 `> [!type]` 格式使用，共 6 种类型：

| 语法 | 类型 | 用途 |
|------|------|------|
| `> [!note]` | Note | 一般补充说明 |
| `> [!tip]` | Tip | 有用的技巧建议 |
| `> [!important]` | Important | 重要信息 |
| `> [!warning]` | Warning | 警告注意 |
| `> [!caution]` | Caution | 危险操作 |
| `> [!info]` | Info | 参考信息 |

## Mermaid 图表

渲染器支持 Mermaid 语法，可嵌入流程图、时序图等。典型场景：

- **流程图**：`graph TD` / `graph LR` 描述工作流或决策树
- **时序图**：`sequenceDiagram` 描述系统交互流程

这些图表为静态文档增加了结构化可视化能力，弥补了纯文字表达的局限。

## 交互式代码块

HTML 和 JavaScript 代码块支持沙盒预览（iframe 隔离），点击「运行」按钮即可查看效果。Python 等其他语言仅提供语法高亮，不支持运行预览。

核心设计要点：
- 沙盒 iframe 隔离运行环境，保障安全性
- 仅 HTML/JS 支持预览（浏览器原生执行）
- 代码高亮采用 OneDark 主题 + 行号显示

## 增强表格

渲染器对表格进行了视觉增强：圆角边框 + 行悬停高亮，优于传统纯文本表格。适合技术对比、属性列举等场景。

## 其他增强

- **引用块**：非 Callout 的 `>` 语法仍渲染为传统斜体引用
- **分隔线**：`---` 分隔上下文
- **行内代码**：变量名、命令、文件路径等标记
- **链接**：标准 Markdown 链接语法
- **复制按钮**：代码块一键复制

## 基础 vs 增强渲染器对比

| 功能 | 基础 Markdown | 增强渲染器 |
|------|--------------|-----------|
| Callout 提示框 | 不支持 | 6 种类型 |
| Mermaid 图表 | 不支持 | 流程图/时序图等 |
| 代码运行预览 | 不支持 | HTML/JS 支持 |
| 代码高亮 | 基础 | OneDark + 行号 |
| 表格样式 | 纯文本 | 圆角边框 + 悬停高亮 |
| 图片 | 原始 | 圆角 + 阴影 + 标题 |
| 复制按钮 | 无 | 一键复制 |

## 相关页面

- [[markdown-进阶语法]] — Markdown 扩展语法的系统梳理（GFM、Frontmatter、Callout、Mermaid、数学公式）
- [[ai-agent-输出格式研究]] — AI Agent 输出格式的结构性错配与 HTML 方案，探讨 Markdown 线性输出的局限与富文本替代方案
