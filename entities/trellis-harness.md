---
title: Trellis — AI Coding Agent Harness
created: 2026-05-14
updated: 2026-05-14
type: entity
tags: [ai-tool, coding-assistant, framework, workflow, agent, open-source, multi-agent]
sources: [raw/articles/2026-05-14-trellis-harness.md]
confidence: high
---

# Trellis — AI Coding Agent Harness

**Trellis** 是一个跨平台 AI Coding Agent 协作框架，在项目 repo 中建立 `.trellis/` 结构层，让不同 AI 编码工具共享规范、任务、记忆和子 agent 能力。由 [Mindfold](https://github.com/mindfold-ai) 开发，AGPL-3.0 开源。^[raw/articles/2026-05-14-trellis-harness.md]

## 核心数据（2026-05-14）

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 7,893 |
| 🍴 Forks | 431 |
| 🐛 Open Issues | 10 |
| 📦 npm 包 | `@mindfoldhq/trellis` v0.5.15 |
| 📥 月下载 | 16,730 |
| 🔤 语言 | TypeScript (monorepo, pnpm) |
| 📜 License | AGPL-3.0 |
| 🏠 文档 | https://docs.trytrellis.app |
| 📅 创建 | 2026-01-26 |

## 核心价值

Trellis 解决的核心问题：**AI 编码 Agent 缺乏持久上下文和可复现工作流**。

| 能力 | 解决什么 |
|------|----------|
| 自动注入规范 | 写一次 `.trellis/spec/`，每会话自动注入，不再反复说明 |
| 任务驱动 | PRD + 实现 + 审查上下文结构化存放在 `.trellis/tasks/` |
| 项目记忆 | `.trellis/workspace/` journal 保存跨会话历史 |
| 团队共享 | 规范在 repo 中，一人优化全队受益 |
| 多平台统一 | 同一结构适配 14 个 AI coding 平台 |

## 四阶段工作流

```
Plan → Implement → Verify → Finish
 ↓        ↓          ↓        ↓
brainstorm implement  check   update-spec
research  (subagent) (subagent) → 新经验回写 spec
→ PRD.md  → 代码     → diff审查+lint/test自修 → 下次更聪明
```

1. **Plan** — `trellis-brainstorm` 逐问引导写 PRD；研究派 `trellis-research` 子 agent
2. **Implement** — 子 agent 按 PRD + 注入 spec 写代码（不自动 commit）
3. **Verify** — `trellis-check` 审查 diff + lint/type-check/test，能自修则自修
4. **Finish** — 最终检查 + `trellis-update-spec` 将新经验回写 spec

## 项目结构

```
.trellis/
├── config.yaml       # 项目级配置
├── workflow.md       # 工作流定义
├── spec/             # 分域规范（按 package/layer）
├── agents/           # 子 agent prompt (check/implement/research)
├── scripts/          # Python 工具 (task.py, get_context.py, hooks/)
├── tasks/            # 活跃任务 (prd.md + jsonl context)
└── workspace/        # 每人 journal + session trace
```

每个平台有独立适配目录（`.cursor/` `.claude/` `.codex/` `.opencode/` `.pi/`），包含 agents、hooks、commands、skills。

## 支持平台（14 个）

Claude Code、Cursor、Codex、OpenCode、Pi (Cognition)、Windsurf、Cline、Gemini CLI、GitHub Copilot、Kilo Code 等。

## 与同类项目的区别

| 对比项 | CLAUDE.md / AGENTS.md | Trellis |
|--------|----------------------|---------|
| 规范组织 | 单文件易"大杂烩" | 分域 spec + 按任务注入 |
| 任务结构 | 无 | PRD + jsonl 结构化管理 |
| 跨会话记忆 | 依赖 LLM | workspace journal 持久化 |
| 多平台 | 各自独立配置 | 统一结构生成 |

## 关联实体

- [[rtk-token-killer]] — 另一个 AI coding 工具链优化项目（token 层面），Trellis 优化工作流层面
- [[hermes-agentic-workflows]] — Hermes 的 agentic 模式体系，与 Trellis 的四阶段工作流互补
- [[hermes-subagent-orchestration]] — Hermes 的子 agent 编排 vs Trellis 的 implement/check/research 子 agent
- [[graphify]] — 知识图谱工具，Trellis 的 spec 系统可视为结构化知识管理的另一种形态
- [[codex-vs-claude-code-operator]] — Codex vs Claude Code 对比，Trellis 横跨两者