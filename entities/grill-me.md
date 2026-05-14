---
title: grill-me
created: 2026-05-14
updated: 2026-05-14
type: entity
tags: [ai-tool, skill-system, agent, claude-code]
sources: [raw/articles/2026-05-14-grill-me-skill.md]
---

# grill-me

> Claude Code / Cowork skill: interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree.^[raw/articles/2026-05-14-grill-me-skill.md]

## 概述

**grill-me** 是一个为 Claude Code 和 AI Cowork 工具设计的 Skill（技能插件），由 RobMitt 开发。它的核心理念是 **"魔鬼代言人"** — 无情地追问用户计划中的每一个细节，沿着决策树的每个分支逐步推进，直到双方达成完全共识。

## 核心机制

1. **逐个追问** — 每次只问一个问题，等回答后再继续，避免信息过载
2. **多选项引导** — 提供 2-4 个具体选项（而非泛泛的 Yes/No），用户也可自定义回答
3. **自动查代码** — 能通过探索代码库解答的问题，自己查而不问用户
4. **决策树遍历** — 沿着设计的每个分支和依赖关系，逐一解决
5. **总结输出** — 所有分支理完后，输出一份简洁的决策汇总

## 安装

将 `SKILL.md` 放入技能目录：

```
~/.claude/skills/grill-me/SKILL.md
```

触发方式：对 AI 说 "grill me" 或要求 stress-test 一个计划。

## 适用场景

- 想压力测试自己的计划或设计
- 把模糊的想法逼到清晰
- 暴露计划中的遗漏决策点
- 设计评审前的自我检查

## 相关变体

- **grill-me-fix** ([dexuwang627-cloud/grill-me-fix](https://github.com/dexuwang627-cloud/grill-me-fix), ⭐3) — 将模糊的视觉感受转化为精确的代码变更。AI 定位代码，把描述翻译为技术根因供选择，确认后才修改。

## 项目数据

| 属性 | 值 |
|------|-----|
| 仓库 | RobMitt/grill-me-skill |
| Stars | 9 |
| Forks | 4 |
| 创建日期 | 2026-04-11 |
| 最近更新 | 2026-05-14 |
| 许可证 | 无 |
| 文件结构 | README.md + SKILL.md |

## 关联概念

- [[claude-code]] — grill-me 是 Claude Code 的 skill 插件，依赖其 Skill 系统运行
- [[skill-system]] — grill-me 展示了 skill 的典型结构：SKILL.md frontmatter + 行为指令
- [[hermes-subagent-orchestration]] — grill-me 的逐层追问模式与子代理编排中的两阶段审查有相似的"逐步确认"哲学
- [[anthropic-prompting-best-practices]] — grill-me 的多选项提问策略呼应了 Anthropic 推荐的结构化交互模式