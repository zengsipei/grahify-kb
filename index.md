# Wiki Index

> Content catalog. Every wiki page listed under its type with a one-line summary.
> Read this first to find relevant pages for any query.
> Last updated: 2026-05-23 | Total pages: 49

## Entities
<!-- Alphabetical within section -->
- [[agentation]] — 传统 AI 编码流程中，用户给 Agent 的反馈是纯文本——"把侧边栏那个蓝色按钮改小一点"——Agent 需要从自然语言猜测目标元素，经常找错。**Agentation 反过来**：用户直接在浏览器页面上点击元素、框选区域、添加批...
- [[browser-harness]] — **Browser Harness** 是 browser-use 团队推出的自愈型（Self-healing）轻量浏览器控制框架，专为 LLM Agent 设计。
- [[claude-使用指南]] — Claude 是 Anthropic 公司开发的大语言模型，以其安全性和长上下文能力著称。本页面汇总了 Claude 的核心使用技巧和最佳实践。
- [[cursor-debug]] — 11|
- [[gemini-使用指南]] — Google Gemini 系列模型的使用方法和最佳实践。
- [[gitnexus]] — 零服务器代码智能引擎。将代码库索引为知识图谱，通过 MCP 或 CLI 暴露给 AI agent，让 agent 改代码时能追踪依赖链、调用链和影响范围。
- [[gpt-使用指南]] — 全面介绍 OpenAI GPT 系列模型的使用方法、最佳实践和高级技巧。
- [[graphify]] — **Graphify** 是 Karpathy LLM Wiki 理念的产品化实现 —— 一个给人看的双链知识图谱工具。
- [[grill-me]] — **grill-me** 是一个为 Claude Code 和 AI Cowork 工具设计的 Skill（技能插件），由 RobMitt 开发。它的核心理念是 **"魔鬼代言人"** — 无情地追问用户计划中的每一个细节，沿着决策树...
- [[hereos-ai]] — CURIOSITY AI 公司的实验性产品，定位「世界首个 GUI 交互驱动的 Agent」。核心理念：Agent 输出不再是静态文本/代码，而是可操作的交互界面。Slogan：「点击，说话 · 告别打字」。
- [[obscura-browser]] — **Obscura** 是用 Rust 编写的开源无头浏览器引擎，专为 AI Agent 自动化和大规模网页爬取设计。
- [[open-design]] — Open Design 遵循六大设计原则：
- [[opus-使用指南]] — Opus 是 z.ai 平台提供的 AI Agent 开发环境，基于强大的 LLM 模型，支持代码生成、文档处理、网页浏览等多种能力。本页面汇总了 Opus 的核心功能和最佳实践。
- [[plannotator]] — Plannotator 解决的问题是：AI Agent 在执行代码修改前通常会先制定计划（Plan），但用户只能通过纯文本阅读和回复来审批计划——既不直观，也没有结构化的反馈机制。
- [[pretext]] — Cheng Lou（前 React 核心成员、Midjourney 现任）开发的纯 TypeScript 文本测量库。绕过浏览器 DOM reflow，用 `Canvas.measureText` 做一次性字体分析后纯算术计算文本布局...
- [[prisma-orm-使用指南]] — Prisma 是下一代 TypeScript ORM，提供类型安全的数据库访问。
- [[rtk-token-killer]] — **rtk** 是一个高性能 CLI 代理，拦截并压缩命令输出再送给 LLM，减少 token 消耗 60-90%。单个 Rust 二进制、零依赖、<10ms 开销。^[raw/articles/2026-05-14-rtk-toke...
- [[stitch2]] — Google Labs 的 AI UI 设计工具，前身为 Galileo AI（2025 年 Google I/O 收购后更名）。2026 年 3 月 18 日发布 2.0 重大更新。被视为 Figma 的强力竞品（更新后 Figma...
- [[tailwindcss-实战技巧]] — Tailwind CSS 4 的实战经验和高级用法。
- [[trellis-harness]] — **Trellis** 是一个跨平台 AI Coding Agent 协作框架，在项目 repo 中建立 `.trellis/` 结构层，让不同 AI 编码工具共享规范、任务、记忆和子 agent 能力。由 [Mindfold](ht...
- [[windsurf-codemaps]] — Windsurf（原 Codeium）推出的 Codemaps 功能，为 AI 编程助手提供代码库的全局视图。
- [[向量数据库入门]] — 向量数据库是存储和检索高维向量的专用数据库，是 [[rag-检索增强生成]] 系统的核心组件。
- [[暗壳ai]] — 国内专业的室内 AI 设计平台（ark.art），2024 年正式上线，2026 年 3 月 31 日发布 Agent 2.0。定位「设计师的万能 AI 工具箱」，覆盖从创意 → 方案 → 采购 → 落地的全链路。

## Concepts

- [[agent-架构设计模式]] — AI Agent 是能够自主感知、推理和行动的 AI 系统。本文总结主流的 Agent 架构设计模式，涵盖核心组件、经典模式、记忆系统与工具设计原则。
- [[ai-agent-输出格式研究]] — 传统 AI 输出是纯文本（Markdown），这是线性的一维格式。但人类认知是二维的、交互的、视觉的。这造成了 AI 输出与人类理解之间的结构性错配。
- [[ai-安全与对齐]] — AI 安全与对齐（Alignment）是确保 AI 系统行为符合人类意图和价值观的关键领域。
- [[anthropic-prompting-best-practices]] — Anthropic 官方提示工程最佳实践（2026-04 更新至 Opus 4.7），把提示词当作可测量、可复用、可迭代的接口设计。
- [[codex-cli-goal]] — OpenAI Codex CLI v0.128.0（2026-04-30）新增的目标生命周期管理命令。Greg Brockman 称其为「built-in Ralph loop++」。核心：将「回答 prompt」升级为「追求结果」，...
- [[function-calling-实践指南]] — Function Calling（工具调用）是 LLM 与外部系统交互的核心机制，让 AI Agent 能够执行实际操作。
- [[git-工作流最佳实践]] — 团队协作中使用 Git 的最佳实践，涵盖分支管理、提交规范和常用技巧。在 AI 辅助开发场景下，规范的 Git 工作流是 [[hermes-agentic-workflows]] 中多代理协作与自动化部署的基础。
- [[hermes-agentic-workflows]] — 将 Claude Code 的 **Operator 三维框架**映射到 Hermes 的实现，同时揭示 Hermes 独有的第四维度。
- [[hermes-cron-headless]] — Hermes 对 Claude Code Headless 模式的根本性扩展——从单次执行升级为**持久化编排流水线**。
- [[hermes-kanban-orchestrator]] — 对比 Claude Code 的 Lead-Teammate 模式与 Hermes 的 `kanban orchestrator`。
- [[hermes-parallel-isolation]] — 对比 Claude Code 的 Worktree 与 Hermes 的 `--worktree` + `--backend` 隔离策略。
- [[hermes-subagent-orchestration]] — 对比 Claude Code 的 Subagent 编排与 Hermes 的 `delegate_task` + 两阶段审查。
- [[llm-评测方法]] — 如何科学地评估大语言模型的输出质量，选择最适合业务的模型。
- [[markdown-渲染增强演示]] — 本页面梳理 Wiki 系统 Markdown 渲染器的增强功能，展示超越基础 Markdown 的渲染能力。这些增强是 [[markdown-进阶语法]] 的实践落地，也与 [[ai-agent-输出格式研究]] 中讨论的"富文本输出...
- [[markdown-进阶语法]] — Markdown 的进阶语法和扩展功能，涵盖 GFM、Frontmatter、Callout 和 Mermaid 图表。
- [[nextjs-最佳实践]] — 基于 Next.js 16 App Router 的开发最佳实践总结。Next.js 作为全栈 React 框架，在 [[知识库架构设计]] 中常被选作 Wiki/文档系统的前端技术栈，也可用于构建 [[暗壳ai]] 类 AI 设计平...
- [[prompt-engineering-最佳实践]] — Prompt Engineering 是与大语言模型（LLM）高效交互的核心技能。本页面总结了经过验证的提示词工程技巧和模式。
- [[rag-检索增强生成]] — RAG（Retrieval-Augmented Generation）通过检索外部知识来增强 LLM 的回答质量，是当前企业级 AI 应用的主流架构。
- [[system-prompt-设计指南]] — System Prompt 是控制 AI 模型行为的核心手段。好的 System Prompt 可以显著提升输出质量。
- [[the-unreasonable-effectiveness-of-html]] — 传统观念认为 AI 的输出应该是「文本」——一段回答、一份报告、一堆代码片段。但本文提出一个反直觉的论点：**HTML 作为 AI 输出格式，其有效性远超直觉预期。**
- [[知识库架构设计]] — LLM Wiki 项目的知识库架构设计决策与演进历程，核心围绕「md 做记忆，html 做展示」的理念，确保内容的持久性、可追溯性和可恢复性。
- [[知识管理系统设计]] — 个人知识管理（PKM）系统的设计理念和方法论，以及如何用技术实现。

## Comparisons

- [[ai-绘画工具对比]] — 主流 AI 绘画工具的功能对比和使用指南。与 [[stitch2]]、[[暗壳ai]] 等 AI 设计工具互补，本页聚焦通用图像生成工具的横向对比。
- [[ai-编程工具对比]] — 全面对比主流 AI 辅助编程工具的优劣势和适用场景。
- [[stitch2-vs-暗壳ai]] — AI 设计工具的两条路线：通用 UI 设计（Google Stitch）vs 垂直室内设计（暗壳AI）。
- [[supabase-vs-firebase]] — 开源 Postgres 后端 vs Google 全托管 BaaS。

## Queries

## Raw Sources (55 files)
- `2026-05-05-claude-code-operator模式.md` — 2026-05-05-claude-code-operator模式
- `2026-05-05-cursor-debug.md` — 2026-05-05-cursor-debug
- `2026-05-05-gitnexus.md` — 2026-05-05-gitnexus
- `2026-05-05-graphify.md` — 2026-05-05-graphify
- `2026-05-05-obscura-browser.md` — 2026-05-05-obscura-browser
- `2026-05-05-pretext-text-measurement.md` — 2026-05-05-pretext-text-measurement
- `2026-05-05-stitch2-AI设计.md` — 2026-05-05-stitch2-AI设计
- `2026-05-05-暗壳AI室内设计.md` — 2026-05-05-暗壳AI室内设计
- `2026-05-06-anthropic-prompting-best-practices.md` — 2026-05-06-anthropic-prompting-best-practices
- `2026-05-06-codex-cli-goal命令.md` — 2026-05-06-codex-cli-goal命令
- `2026-05-06-hereos-ai.md` — 2026-05-06-hereos-ai
- `2026-05-07-browser-harness.md` — 2026-05-07-browser-harness
- `2026-05-07-supabase-firebase.md` — 2026-05-07-supabase-firebase
- `2026-05-07-windsurf-codemaps.md` — 2026-05-07-windsurf-codemaps
- `2026-05-09-hermes-operator-pattern.md` — Hermes Agent 中的 Operator 模式：三维框架与 Claude Code 的深度对比
- `2026-05-14-grill-me-skill.md` — grill-me-skill
- `2026-05-14-rtk-token-killer.md` — rtk-ai/rtk — Rust Token Killer
- `2026-05-14-trellis-harness.md` — mindfold-ai/Trellis — AI Coding Agent Harness
- `2026-05-23-agent-架构设计模式.md` — Agent 架构设计模式
- `2026-05-23-agentation-ai-编码-agent-的视觉反馈工具.md` — Agentation — AI 编码 Agent 的视觉反馈工具
- `2026-05-23-ai-agent-输出格式研究.md` — AI Agent 输出格式研究
- `2026-05-23-ai-安全与对齐.md` — AI 安全与对齐
- `2026-05-23-ai-绘画工具对比.md` — AI 绘画工具对比
- `2026-05-23-ai-编程工具对比.md` — AI 编程工具对比
- `2026-05-23-anthropic-claude-prompting-best-practices.md` — Anthropic Claude Prompting Best Practices
- `2026-05-23-claude-使用指南.md` — Claude 使用指南
- `2026-05-23-function-calling-实践指南.md` — Function Calling 实践指南
- `2026-05-23-gemini-使用指南.md` — Gemini 使用指南
- `2026-05-23-git-工作流最佳实践.md` — Git 工作流最佳实践
- `2026-05-23-google-stitch-20-ai-ui-设计工具.md` — Google Stitch 2.0 - AI UI 设计工具
- `2026-05-23-gpt-使用指南.md` — GPT 使用指南
- `2026-05-23-hereos-gui-交互驱动的-agent.md` — HereOS — GUI 交互驱动的 Agent
- `2026-05-23-hermes-agent-中的-operator-模式三维框架与-claude-code-的深度对比.md` — Hermes Agent 中的 Operator 模式：三维框架与 Claude Code 的深度对比
- `2026-05-23-llm-评测方法.md` — LLM 评测方法
- `2026-05-23-markdown-渲染增强演示.md` — Markdown 渲染增强演示
- `2026-05-23-markdown-进阶语法.md` — Markdown 进阶语法
- `2026-05-23-mindfold-aitrellis-ai-coding-agent-harness.md` — mindfold-ai/Trellis — AI Coding Agent Harness
- `2026-05-23-nextjs-最佳实践.md` — Next.js 最佳实践
- `2026-05-23-obscura-rust-无头浏览器引擎.md` — Obscura - Rust 无头浏览器引擎
- `2026-05-23-open-design.md` — Open Design
- `2026-05-23-opus-使用指南.md` — Opus 使用指南
- `2026-05-23-plannotator-交互式计划与代码审查.md` — Plannotator — AI Agent 的交互式计划与代码审查工具
- `2026-05-23-pretext-纯-js-文本测量库.md` — Pretext - 纯 JS 文本测量库
- `2026-05-23-prisma-orm-使用指南.md` — Prisma ORM 使用指南
- `2026-05-23-prompt-engineering-最佳实践.md` — Prompt Engineering 最佳实践
- `2026-05-23-rag-检索增强生成.md` — RAG 检索增强生成
- `2026-05-23-rtk-airtk-rust-token-killer.md` — rtk-ai/rtk — Rust Token Killer
- `2026-05-23-supabase-vs-firebase.md` — Supabase vs Firebase
- `2026-05-23-system-prompt-设计指南.md` — System Prompt 设计指南
- `2026-05-23-tailwindcss-实战技巧.md` — Tailwind CSS 实战技巧
- `2026-05-23-the-unreasonable-effectiveness-of-html-html-的不合理有效性.md` — HTML 的不合理有效性
- `2026-05-23-向量数据库入门.md` — 向量数据库入门
- `2026-05-23-暗壳ai-室内ai设计平台.md` — 暗壳AI - 室内AI设计平台
- `2026-05-23-知识库架构设计.md` — 知识库架构设计
- `2026-05-23-知识管理系统设计.md` — 知识管理系统设计