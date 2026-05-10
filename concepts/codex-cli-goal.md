---
title: codex-cli-goal
created: 2026-05-10
updated: 2026-05-10
type: concept
tags: [agent, workflow, coding-assistant, open-source]
sources: [raw/articles/2026-05-06-codex-cli-goal命令.md]
---

# Codex CLI /goal 命令

OpenAI Codex CLI v0.128.0（2026-04-30）新增的目标生命周期管理命令。Greg Brockman 称其为「built-in Ralph loop++」。核心：将「回答 prompt」升级为「追求结果」，Agent 跨多轮自主推进直至完成。

## 5 个控制命令

| 命令 | 作用 |
|------|------|
| `/goal <objective>` | 创建新目标 |
| `/goal pause` | 暂停当前目标 |
| `/goal resume` | 恢复暂停的目标 |
| `/goal clear` | 清空目标 |
| `codex resume <id>` | 跨会话恢复目标 |

## 目标状态机

```
CREATED → PAUSED ⇄ RESUMED → COMPLETED / BUDGET_LIMITED → REMOVED
```

## 五段式黄金模板

1. **Objective** — 要达成什么
2. **Scope** — 范围界定
3. **Constraints** — 约束条件
4. **Done when** — 完成标准（必须引用具体文件路径或命令）
5. **Stop if** — 中止条件
6. **Token budget** — token 预算（软停止：触发后生成收尾报告再停）

## 5 个 PR 的架构

1. 持久化层（`thread_goals` 表）
2. App-Server RPC
3. 模型工具（`get/create/update_goal`）
4. 运行时（空闲延续 + token 计费）
5. TUI

## 安全设计

- 模型**不能**自己暂停或清空目标（仅用户可操作）
- Plan 模式下会静默跳过延续（Issue #20656）
- 第一条消息不要直接用 `/goal`（新会话找不到 thread）

## 与 Wiki 生态的关系

- **[[hermes-agentic-workflows]]** — /goal 是 Agentic 工作流的典型实现，与 Hermes 的多轮推进有直接对应
- **[[hermes-kanban-orchestrator]]** — Kanban 编排器的「任务板 → 独立推进」模式与 /goal 的多轮自主延续异曲同工
- **[[hermes-cron-headless]]** — Cron 流水线的「跨会话持久化」与 /goal 的 `codex resume <id>` 对应
- **[[hermes-subagent-orchestration]]** — 子代理编排中的两阶段审查可嵌入 /goal 流程
- **[[hereos-ai]]** — 对比：目标持久化方式不同（thread_goals vs Agent State）