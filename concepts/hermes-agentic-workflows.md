---
title: Hermes Agentic 工作流模式
created: 2026-05-08
updated: 2026-05-23
type: concept
tags: [operator-mode, agent, workflow, claude-code]
sources: [raw/articles/2026-05-05-claude-code-operator模式.md, raw/articles/2026-05-09-hermes-operator-pattern.md, raw/articles/2026-05-23-hermes-agent-中的-operator-模式三维框架与-claude-code-的深度对比.md]
confidence: high
---

# Hermes Agentic 工作流模式

将 Claude Code 的 **Operator 三维框架**映射到 Hermes 的实现，同时揭示 Hermes 独有的第四维度。

## Claude Code Operator 框架

```
┌──────────────────────────────────────────────────────────┐
│                    Claude Code Operator 框架              │
│                                                          │
│  ┌──────────────┐  ┌──────────────┐  ┌────────────────┐  │
│  │  Worktree    │  │  Subagent    │  │ Lead-Teammate  │  │
│  │  并行隔离    │  │  编排调度    │  │  分工协作      │  │
│  └──────────────┘  └──────────────┘  └────────────────┘  │
│         │                  │                  │           │
│         ▼                  ▼                  ▼           │
│  git worktree       内置+自定义子代理     Shared Task List  │
│  独立 CLAUDE.md     skill discoverability  Interface-First  │
└──────────────────────────────────────────────────────────┘
```

## Hermes 四维框架

| Claude Code 模式 | Token 成本 | Hermes 实现 | 详解 |
|-----------------|-----------|-------------|------|
| Sequential Flow | 1x | `/plan` → `subagent-driven-development` | [[hermes-subagent-orchestration]] |
| Operator | 1.5x | `delegate_task` + `kanban orchestrator` + `cron` | [[hermes-subagent-orchestration]] |
| Split-and-Merge | 3-4x | `--worktree` (`-w`) + `--backend` | [[hermes-parallel-isolation]] |
| Agent Teams | 3-4x | `kanban orchestrator` | [[hermes-kanban-orchestrator]] |
| Headless | 1x | `cron` jobs | [[hermes-cron-headless]] |

## 核心差异：Skill Discoverability

| 维度 | Claude Code（隐式） | Hermes（显式） |
|------|-------------------|--------------|
| 发现方式 | description 匹配 | `skill_view()` 主动加载 |
| Silent failure 风险 | 高 | 无 |
| 可控性 | 低 | 高 |
| 成本 | 无额外调用 | 多几次 skill_view() |

Hermes 把隐式 discoverability 做成显式 gate——代价是多了几次 tool call，收益是完全消除了 "skill 没被发现" 的 silent failure。

## 选择指南

| 场景 | 推荐方案 |
|------|---------|
| 简单修改（< 3 文件） | 直接 terminal/patch |
| 中等功能（3-10 文件） | `/plan` → `delegate_task` |
| 大型重构（10+ 文件） | `kanban orchestrator` |
| 并行独立任务 | `worktree` (`-w`) |
| 跨机器/环境 | `--backend` |
| 定时自动化 | `cron` + `delegate_task` |
| CI/CD 流水线 | `cron` 链式 job |
| 需要人工审批 | `kanban_block()` |

## 黄金法则

> **比你认为需要的更简单开始。** 稳定运行的 Sequential Flow 比偶尔惊艳的 Agent Teams 有价值得多。

## 相关页面

- [[hermes-parallel-isolation]] — 并行隔离模式详解
- [[hermes-subagent-orchestration]] — 子代理编排详解
- [[hermes-kanban-orchestrator]] — Kanban 编排器详解
- [[hermes-cron-headless]] — Cron 流水线详解
- [[cursor-debug]] — Cursor 调试技巧
- [[graphify]] — 知识图谱工具