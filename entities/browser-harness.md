---
title: Browser Harness
created: 2026-05-08
updated: 2026-05-08
type: entity
tags: [tool, browser-automation, cdp, ai-agent, self-healing, skill-system]
sources: [raw/articles/2026-05-07-browser-harness.md]
confidence: high
---

# Browser Harness

**Browser Harness** 是 browser-use 团队推出的自愈型（Self-healing）轻量浏览器控制框架，专为 LLM Agent 设计。

## 概述

- **仓库**: https://github.com/browser-use/browser-harness
- **组织**: browser-use
- **语言**: Python 100%
- **核心代码**: ~1,000 行
- **Stars**: 11.2k+ (2026-05)
- **许可证**: MIT
- **标语**: "You will never use the browser again."

## 核心创新

### 1. 极简架构（"反框架"设计）

browser-use 团队将数万行框架代码推倒重来，只保留：
- 一条直连 Chrome 的 WebSocket 连接
- 4 个核心文件/目录的扁平结构
- 直接暴露 CDP（Chrome DevTools Protocol），无中间抽象层

### 2. 自愈机制（Self-healing）

- Agent 运行时遇到缺失功能 → 自行编写代码并保存到 `agent_helpers.py`
- 每次运行积累改进，harness 越用越强
- 与传统 try-catch-retry 不同：让 AI 成为问题解决者，而非预设逻辑的调用者

### 3. Skill 系统（技能自生成）

- Agent 在执行任务中发现**非显而易见的操作方法**时，自动生成 Skill 文件
- 包含选择器、操作流程、边缘情况处理
- 后续遇到相同网站/任务直接复用，无需重新探索
- 支持 Domain Skills：按网站域名自动加载（`BH_DOMAIN_SKILLS=1`）
- 社区可通过 PR 贡献 domain skills（已有 GitHub、LinkedIn、Facebook、Amazon 等）

## 与 Obscura 的对比

| 维度 | Browser Harness | Obscura |
|------|-----------------|---------|
| 语言 | Python | Rust |
| 架构 | CDP 包装器 | 独立引擎 |
| 特色 | 自愈 + Skill | 轻量 + Stealth |
| 适用 | LLM Agent | 爬虫 + 自动化 |

## Hermes 集成

Hermes 的 `browser` tool 可配合 Browser Harness：
- Browser Harness 提供 MCP server
- Hermes 通过 `mcp` 工具调用，实现浏览器自动化

## 相关页面

- [[obscura-browser]] — 另一个浏览器自动化工具
- [[hermes-agentic-workflows]] — Hermes 的 browser tool 和 MCP 集成
- [[pretext]] — 浏览器文本渲染优化（比 DOM 快 300-600x，虚拟滚动场景）