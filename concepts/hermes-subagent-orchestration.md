---
title: Hermes 子代理编排
created: 2026-05-09
updated: 2026-05-09
type: concept
tags: [agent, workflow, delegate, subagent, orchestration, skill-discoverability]
sources: [raw/articles/2026-05-05-claude-code-operator模式.md, raw/articles/2026-05-09-hermes-operator-pattern.md]
---

# Hermes 子代理编排

对比 Claude Code 的 Subagent 编排与 Hermes 的 `delegate_task` + 两阶段审查。

## Claude Code 的做法

三种内置子代理：
- **Explore Agent**（Haiku，只读）— 搜索文件、读取代码
- **Plan Agent**（只读）— 收集上下文、生成计划
- **General-Purpose Agent**（完整工具）— 读写编辑运行

自定义代理在 `.claude/agents/`，靠 skill description 的"攻击性"匹配来**隐式发现**。

## Hermes 的做法：`delegate_task`

```python
delegate_task(
    goal="实现用户认证模块",
    context="完整规格 + 文件路径 + 约束条件",
    role="leaf",              # 或 "orchestrator" 递归
    toolsets=['terminal', 'file']  # 精确工具集控制
)
```

## 核心升级：两阶段审查

```
每项任务 = 实现者 → 规格审查 → 质量审查 → 完成
```

这解决了 Claude Code 的 **silent failure** 问题。

## 对比表

| 维度 | Claude Code | Hermes |
|------|------------|--------|
| 子代理能力 | 三种内置 + YAML | 动态 toolsets，精确到工具集 |
| 递归 | 实验性 | `role="orchestrator"` 可配置深度 |
| 审查 | 自定义 agent | 两阶段内置审查 |
| 上下文传递 | Mailbox | 结构化 context + 父 session |
| Skill 发现 | 隐式（description matching） | 显式（skill_view 加载） |

## Skill Discoverability 哲学

| 维度 | Claude Code（隐式） | Hermes（显式） |
|------|-------------------|--------------|
| 发现方式 | description 匹配 | `skill_view()` 主动加载 |
| Silent failure 风险 | 高 | 无 |
| 可控性 | 低 | 高 |
| 成本 | 无额外调用 | 多几次 skill_view() |

Hermes 把隐式 discoverability 做成显式 gate——代价是多了几次 tool call，收益是完全消除了 "skill 没被发现" 的 silent failure。

## 相关页面

- [[hermes-agentic-workflows]] — 完整工作流模式概览
- [[hermes-parallel-isolation]] — 并行隔离详解