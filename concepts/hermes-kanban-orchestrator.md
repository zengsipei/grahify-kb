---
title: Hermes Kanban 编排器
created: 2026-05-09
updated: 2026-05-09
type: concept
tags: [agent, workflow, kanban, orchestration, multi-agent]
sources: [raw/articles/2026-05-05-claude-code-operator模式.md, raw/articles/2026-05-09-hermes-operator-pattern.md]
---

# Hermes Kanban 编排器

对比 Claude Code 的 Lead-Teammate 模式与 Hermes 的 `kanban orchestrator`。

## Claude Code：Lead-Teammate

- **Lead Agent**：全局架构判断、任务拆分、接口定义
- **Teammate**：独立 Claude Code 实例，具体执行
- **Shared Task List**：工作项有状态和依赖跟踪
- **Mailbox**：点对点消息传递
- **Interface-First 策略**：先约定接口再并行

## Hermes：Kanban Orchestrator

```python
kanban_create(
    title="synthesize migration recommendation",
    assignee="analyst",
    body="Read findings from cost and performance research...",
    parents=[t1, t2],  # 自动门控
)
```

## 核心机制对比

| 机制 | Claude Code | Hermes |
|------|------------|--------|
| 协调 | Mailbox（实验性） | Specialist roster + 依赖门控 |
| 持久化 | 会话内 | SQLite，跨会话存活 |
| 人工介入 | 手动 | `kanban_block()` 任意步骤暂停 |
| 故障恢复 | 无 | Reclaim/Reassign/Recovery |
| 任务路由 | 靠描述 | 标准化 profile dispatch |

## 标准 Specialist Roster

```
researcher → analyst → writer → reviewer     （知识工作流）
pm → backend-eng → reviewer                  （开发流水线）
pm → backend-eng + frontend-eng → ops        （并行开发）
```

## 依赖门控

子任务只有在所有父任务 (`parents=[...]`) 完成后才自动提升到 `ready`——实现了 Claude Code `interface-first` 策略的自动化。

## 故障恢复

- **Reclaim**：终止错误 worker，重置任务
- **Reassign**：切换到不同 specialist
- **Change model**：换模型重试

## 相关页面

- [[hermes-agentic-workflows]] — 完整工作流模式概览
- [[hermes-cron-headless]] — Cron 流水线详解