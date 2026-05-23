---
title: Anthropic Prompting Best Practices
created: 2026-05-09
updated: 2026-05-23
type: concept
tags: [prompt-engineering, anthropic, claude-code]
sources: [raw/articles/2026-05-06-anthropic-prompting-best-practices.md, raw/articles/2026-05-23-anthropic-claude-prompting-best-practices.md]
---

# Anthropic Prompting Best Practices

Anthropic 官方提示工程最佳实践（2026-04 更新至 Opus 4.7），把提示词当作可测量、可复用、可迭代的接口设计。

## 黄金法则

> **把 Claude 当作"缺乏上下文的新同事"**——如果同事看不懂你的 prompt，Claude 也一样。

## 核心原则

### 1. 解释"为什么"

- ❌ `NEVER use ellipses`
- ✅ `Never use ellipses because the text-to-speech engine cannot pronounce them.`

**原理**：理解因果链后，模型能把规则泛化到其他场景。

### 2. Few-shot 示例（3~5 个最佳）

- 要相关、多样、用 `<example>` 标签包裹
- 更多示例会稀释指令、降低泛化能力

### 3. XML 标签结构化

```xml
<documents>
  <document index="1">
    <source>file.pdf</source>
    <document_content>{{CONTENT}}</document_content>
  </document>
</documents>

Analyze the document and answer the question.
```

**要点**：给模型一棵可解析的"文档树"，标签名要一致且有语义。

### 4. 显式标准

- ❌ `Create an analytics dashboard`
- ✅ `Create an analytics dashboard. Include as many relevant features and interactions as possible.`

## 关键技巧

| 技巧 | 说明 |
|------|------|
| 角色设定 | 明确"你是谁"（专家/初学者/审稿人） |
| 任务分解 | 复杂任务拆成步骤 |
| 输出格式 | 指定格式（JSON/Markdown/表格） |
| 思维链 | `Let's think step by step` |
| 自检 | `Check your answer for errors` |

## 相关页面

- [[hermes-agentic-workflows]] — Hermes 的 prompt 设计原则
- [[hermes-subagent-orchestration]] — 子代理编排的 prompt 技巧