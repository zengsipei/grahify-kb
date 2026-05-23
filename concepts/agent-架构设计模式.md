---
title: Agent 架构设计模式
created: 2026-05-23
updated: 2026-05-23
type: concept
tags: [agent, workflow, ai-agent]
sources: [raw/articles/2026-05-23-agent-架构设计模式.md]
---

# Agent 架构设计模式

AI Agent 是能够自主感知、推理和行动的 AI 系统。本文总结主流的 Agent 架构设计模式，涵盖核心组件、经典模式、记忆系统与工具设计原则。

## 核心组件

一个典型的 AI Agent 由三大核心组件构成：

```
┌─────────────────────────────┐
│         AI Agent            │
│  ┌───────┐  ┌───────────┐  │
│  │ LLM   │  │  Memory   │  │
│  │ 推理引擎│  │ 上下文管理 │  │
│  └───┬───┘  └───────────┘  │
│      │                      │
│  ┌───▼─────────────────┐   │
│  │    Tool Registry     │   │
│  │ 搜索 / 代码 / API    │   │
│  └─────────────────────┘   │
└─────────────────────────────┘
```

- **LLM 推理引擎**：负责理解、规划和决策
- **Memory 上下文管理**：维护对话历史与知识状态
- **Tool Registry**：注册可调用的工具（搜索、代码执行、API 调用等）

## ReAct 模式

**Reasoning + Acting**，最经典的 Agent 模式。

> **核心思想**：模型交替进行"思考"和"行动"，每次行动后观察结果，再决定下一步。

```
Question: 用户注册页面报错 500

Thought: 需要先查看服务端日志
Action: run_command("tail -n 50 /var/log/app.log")
Observation: [ERROR] Database connection timeout

Thought: 数据库连接超时，检查连接池配置
Action: read_file("config/database.py")
Observation: pool_size=5, max_overflow=10

Thought: 连接池配置偏小，建议增大
Answer: 问题原因是数据库连接池过小导致高并发时超时。建议将 pool_size 从 5 增大到 20。
```

ReAct 的优势在于**可观测性**——每一步推理和行动都可见，便于调试和审计。Hermes 的 agentic workflow 在 [[hermes-agentic-workflows]] 中大量采用此模式。

## Plan-and-Execute 模式

先规划再执行，适合"有明确目标但路径不确定"的复杂任务（如"重构认证模块"）。

```python
async def plan_and_execute(task: str):
    # 1. 制定计划
    plan = await llm.generate(f"将以下任务分解为步骤:\n{task}")
    steps = parse_steps(plan)
    
    # 2. 逐步执行
    results = []
    for step in steps:
        result = await execute_step(step)
        results.append(result)
        
        # 3. 根据执行结果调整计划
        if result.needs_replan:
            plan = await llm.generate(f"根据执行结果调整计划:\n{result}")
            steps = parse_steps(plan)
    
    return results
```

关键特征：
- **分治策略**：将复杂任务分解为可执行的子步骤
- **动态调整**：执行结果可以触发重新规划
- **与 [[hermes-subagent-orchestration]] 的关联**：Hermes 的 delegate_task 机制本质上是 Plan-and-Execute 的子代理实现——主代理规划，子代理执行

## Multi-Agent 模式

多个 Agent 协作完成复杂任务，常见协作模式：

| 模式 | 说明 | 适用场景 |
|------|------|---------|
| 串行流水线 | Agent A → Agent B → Agent C | 文档处理管线 |
| 并行处理 | 多个 Agent 同时工作 | 多维度分析 |
| 辩论模式 | Agent 互相对抗评审 | 方案评审 |
| 层级管理 | Manager Agent 分配任务 | 复杂项目管理 |

### 示例：代码审查 Multi-Agent

```
User: 审查这段代码

Manager Agent: 
  → Security Agent: 检查安全漏洞
  → Performance Agent: 检查性能问题
  → Style Agent: 检查代码规范

Manager Agent: 汇总三个 Agent 的反馈，给出综合评价
```

Multi-Agent 模式与 [[ai-agent-输出格式研究]] 密切相关——多 Agent 间需要结构化的输出格式来确保协作的有效性。

## 记忆系统

| 类型 | 存储 | 保留时间 | 示例 |
|------|------|---------|------|
| Working Memory | 对话上下文 | 单次会话 | 当前对话历史 |
| Short-term | 向量数据库 | 数天/数周 | 最近操作记录 |
| Long-term | 知识库/文档 | 永久 | 项目文档、用户偏好 |

记忆系统的设计直接影响 Agent 的**上下文窗口利用率**和**长期一致性**。

## 工具设计原则

1. **单一职责**：每个工具只做一件事
2. **清晰描述**：工具名称和描述要让 LLM 理解何时使用
3. **错误处理**：返回有意义的错误信息
4. **幂等性**：相同输入应返回相同结果
5. **安全边界**：限制工具的权限范围

## 相关概念

- [[hermes-agentic-workflows]] — Hermes Agentic 工作流模式：四维框架总览，将 ReAct、Plan-and-Execute 等模式映射为具体实现
- [[ai-agent-输出格式研究]] — AI Agent 输出格式研究，Multi-Agent 协作中的结构化输出设计
- [[hermes-subagent-orchestration]] — 子代理编排：delegate_task + 两阶段审查，Plan-and-Execute 的工程化实践
