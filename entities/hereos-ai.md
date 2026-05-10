---
title: hereos-ai
created: 2026-05-10
updated: 2026-05-10
type: entity
tags: [ai-tool, agent, gui, open-source]
sources: [raw/articles/2026-05-06-hereos-ai.md]
---

# HereOS

CURIOSITY AI 公司的实验性产品，定位「世界首个 GUI 交互驱动的 Agent」。核心理念：Agent 输出不再是静态文本/代码，而是可操作的交互界面。Slogan：「点击，说话 · 告别打字」。

**GitHub：** [charliechen11/here-os-releases](https://github.com/charliechen11/here-os-releases) | **阶段：** Research Preview（免费 Waitlist）

## 核心架构：双层状态机

| 层 | 职责 |
|----|------|
| **Agent State** | Agent 产出，驱动 UI 更新 |
| **UI State** | 用户操作，反馈回 Agent |

两层状态机循环：Agent 产出界面 → 用户操作反馈 → Agent 调整策略 → 更新界面。

## 交互方式

GUI 点击 + 语音，完全脱离 CLI/chat 范式。目标是让用户「根本不需要 prompt engineering」。

## 平台限制

macOS only（Apple Silicon M 系列），通过 GitHub Releases 分发 .dmg。2026-05-04 同日发布 v1.0.1~v1.0.5。

## 与 Wiki 生态的关系

- **[[codex-cli-goal]]** — 交互方式对比：GUI vs CLI；输出形式：可操作界面 vs 代码/文本；目标持久化：Agent State vs thread_goals 表
- **[[hermes-agentic-workflows]]** — 双层状态机是 Agent 工作流的新范式，与 Hermes subagent 编排形成对比（GUI vs CLI）
- **[[anthropic-prompting-best-practices]]** — HereOS 的终极目标是让用户不再需要 prompt engineering
- **[[browser-harness]]** — 同为 Agent 工具生态
- **[[cursor-debug]]** — 同为 Agent 工具生态的组成部分

## 已知局限

极早期（0 stars、0 forks）、大量未知信息（底层模型、架构细节、商业模式）。