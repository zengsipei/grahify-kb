---
title: pretext
created: 2026-05-10
updated: 2026-05-10
type: entity
tags: [ai-tool, tool, browser, framework, open-source]
sources: [raw/articles/2026-05-05-pretext-text-measurement.md]
---

# Pretext

Cheng Lou（前 React 核心成员、Midjourney 现任）开发的纯 TypeScript 文本测量库。绕过浏览器 DOM reflow，用 `Canvas.measureText` 做一次性字体分析后纯算术计算文本布局，比 DOM 测量快 300–600 倍，Gzip 仅 5KB。

**GitHub：** 发布一周 10k+ stars | **官网：** [pretextjs.net/zh](https://pretextjs.net/zh)

## 核心设计

两阶段设计：

1. **`prepare()`** — 一次性字体分析（1–5ms），测量所有需要的字形度量
2. **`layout()`** — 纯算术计算文本布局（~0.0002ms/次），无需 DOM

用 `Intl.Segmenter` 做 Unicode 分词，正确支持 CJK、泰语、阿拉伯语 RTL、Emoji 序列。

## 适用场景

- 虚拟滚动（大量文本高性能布局）
- 防止 CLS（Layout Shift，计算精确高度预占位）
- Canvas/WebGL 文本渲染
- 障碍物感知文字排版

## 运行环境

浏览器、Node.js、Web Worker、SSR 均可运行。

## 已知限制

- 依赖 Canvas API（Node 环境需 `canvas` 包）
- 不支持 `white-space: pre-wrap`

## 与 Wiki 生态的关系

- 与现有 wiki 核心主题（编码助手、知识管理）直接关联较弱，但属于 AI/ML 工具链的前端基础设施层
- 可用于编码助手（[[cursor-debug]]、Codex CLI）生成的 Web 应用性能优化
- 与 [[graphify]] 无直接关联