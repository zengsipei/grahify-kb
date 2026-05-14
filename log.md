# Wiki Log

> Chronological record of all wiki actions. Append-only.
> Format: `## [YYYY-MM-DD] action | subject`
> Actions: ingest, update, query, lint, create, archive, delete
> When this file exceeds 500 entries, rotate: rename to log-YYYY.md, start fresh.

## [2026-05-08] create | Wiki initialized
- Domain: AI/ML 工具、编码助手、浏览器自动化、知识管理、Web 开发
- Structure: raw/ + entities/ + concepts/ + comparisons/ + queries/ + graphify-out/
- Migrated 15 raw sources from grahify-kb
- Migrated 1 wiki page (cursor-debug) from grahify-kb
- Copied graphify-out/ from grahify-kb (90 nodes, 94 edges, 11 communities)

## [2026-05-08] ingest | grahify-kb raw sources
- Files: 2026-05-05-* (7), 2026-05-06-* (3), 2026-05-07-* (3), 暗壳AI室内设计 (1)
- Source: https://github.com/zengsipei/grahify-kb

## [2026-05-08] create | hermes-agentic-workflows concept
- New concept page: concepts/hermes-agentic-workflows.md
- Maps Claude Code's 5 operator patterns to Hermes implementations:
  - Sequential Flow → /plan
  - Operator → delegate_task
  - Split-and-Merge → --worktree
  - Agent Teams → kanban-orchestrator
  - Headless → cron jobs
- Cross-references cursor-debug and graphify

## [2026-05-08] create | Entity pages for tools
- entities/graphify.md — Knowledge graph tool (Karpathy LLM Wiki productized)
- entities/obscura-browser.md — Rust headless browser engine
- entities/browser-harness.md — Self-healing browser control framework
- Updated index.md with new entities

## [2026-05-09] ingest | Hermes Operator 模式深度分析
- New raw source: raw/articles/2026-05-09-hermes-operator-pattern.md
- 全面对比 Hermes 与 Claude Code 的 Operator 三维框架：
  - 维度一：Parallel Isolation（--worktree → --backend 后端级隔离）
  - 维度二：Subagent Orchestration（delegate_task + 两阶段审查 → vs skill discoverability）
  - 维度三：Lead-Teammate（kanban orchestrator + 依赖门控 → vs Mailbox）
  - 维度四（Hermes 独有）：Cron-Driven Headless Operator
  - Skill Discoverability 哲学对比：隐式 vs 显式
- Updated concepts/hermes-agentic-workflows.md:
  - 整合 Claude Code 三维框架 + Hermes 四维实现
  - 新增 Skill Discoverability 对比分析
  - 新增实践案例和反模式指南
  - 更新 tags 加入 operator-mode, skill-discoverability
- Split oversized hermes-agentic-workflows.md (276 lines) into 4 pages:
  - concepts/hermes-agentic-workflows.md (概览页，76 lines)
  - concepts/hermes-parallel-isolation.md (并行隔离详解)
  - concepts/hermes-subagent-orchestration.md (子代理编排详解)
  - concepts/hermes-kanban-orchestrator.md (Kanban 编排详解)
  - concepts/hermes-cron-headless.md (Cron 流水线详解)
- Fixed cursor-debug.md:
  - Removed broken [[gitnexus]] link (page not yet created)
  - Fixed frontmatter to comply with schema
- Updated SCHEMA.md: Extended tag taxonomy to include all used tags
- Updated index.md (16 raw sources, total pages: 9)

## [2026-05-09] create | 新增 3 个 wiki 页面
- concepts/anthropic-prompting-best-practices.md — Anthropic 官方提示工程最佳实践
- entities/windsurf-codemaps.md — Windsurf Codemaps 代码地图功能
- comparisons/supabase-vs-firebase.md — Supabase vs Firebase 对比
- Updated index.md (total pages: 12)

## [2026-05-10] create | 补充缺失页面（7 个）

- 新建 5 个 entity 页面：
  - entities/gitnexus.md — 零服务器代码智能引擎（MCP + 知识图谱）
  - entities/pretext.md — Cheng Lou 纯 TS 文本测量库
  - entities/stitch2.md — Google Labs AI UI 设计工具（Figma 竞品）
  - entities/暗壳ai.md — 国内专业室内 AI 设计平台
  - entities/hereos-ai.md — 首个 GUI 交互驱动的 Agent
- 新建 1 个 concept 页面：
  - concepts/codex-cli-goal.md — Codex CLI /goal 目标生命周期管理
- 新建 1 个 comparison 页面：
  - comparisons/stitch2-vs-暗壳ai.md — 通用 UI 设计 vs 垂直室内设计对比
- 页面互链：stitch2 ↔ 暗壳ai ↔ stitch2-vs-暗壳ai，codex-cli-goal ↔ hermes 四子页面 + hereos-ai
- 更新 index.md（total pages: 12 → 19）

## [2026-05-10] lint | Wiki 健康检查

- 运行 lint：修复 8 个问题
  - 移除 broken link: codex-cli-goal → codex-goal-vs-hereos
  - 扩展 SCHEMA.md 标签：mcp, gui, ide, anthropic
  - 修复无效标签：anthropic-prompting-best-practices, supabase-vs-firebase, windsurf-codemaps
  - 添加 inbound links：supabase-vs-firebase（← graphify）, pretext（← browser-harness）
- Lint 通过：0 issues

## [2026-05-10] update | Graphify 知识图谱更新

- 运行 `graphify update .`
- 图谱更新：90→368 nodes, 94→334 edges, 11→47 communities

## [2026-05-11] ingest | Codex Subagents + Worktrees 官方文档 + 对比分析

- 新建 1 个 raw source：`raw/articles/2026-05-11-codex-subagents-worktrees.md`
  - 来源：developers.openai.com/codex/subagents + developers.openai.com/codex/worktrees
- 新建 1 个概念页面：`concepts/codex-vs-claude-code-operator.md`
  - 类型：比较（Codex vs Claude Code Operator 三维对应）
  - 内容：三维对照总览、Worktrees/Subagents/Lead-Teammate 逐一对比、完整对比矩阵
- 更新 index.md（total pages: 19 → 20, raw sources: 16 → 17）
- 运行 `graphify update .`：428 nodes, 392 edges, 49 communities

## [2026-05-14] ingest | rtk-ai/rtk — Rust Token Killer
- 新 source: `raw/articles/2026-05-14-rtk-token-killer.md`
  - 来源: https://github.com/rtk-ai/rtk
  - GitHub API 获取仓库元数据 + release info + readme 原文
  - Stars: 47,271 / Forks: 2,862 / License: Apache-2.0 / Language: Rust
- 新建 1 个实体页面: `entities/rtk-token-killer.md`
  - 类型：工具实体（AI 编码工具 / LLM token 优化）
  - 核心内容：rtk 工作原理（四大压缩策略）、100+ 命令覆盖、13 个 AI 工具集成
  - 与其它 Rust 工具关联：[[obscura-browser]]、[[pretext]]、[[hermes-agentic-workflows]]
  - Hermes 集成：`rtk init --agent hermes` → Python 插件适配器
- 更新 index.md（total pages: 20 → 21, raw sources: 17 → 18）

## [2026-05-14] ingest | RobMitt/grill-me-skill — AI 追问决策树 skill
- 新 source: `raw/articles/2026-05-14-grill-me-skill.md`
  - 来源: https://github.com/RobMitt/grill-me-skill
  - GitHub API 获取仓库元数据 + README.md + SKILL.md 全文
  - Stars: 9 / Forks: 4 / License: 无 / Language: 无（skill 文件）
- 新建 1 个实体页面: `entities/grill-me.md`
  - 类型：工具实体（AI 编码 skill / 决策树追问）
  - 核心内容：grill-me 工作机制（逐个追问、多选项引导、自动查代码、决策树遍历、总结输出）、安装方式、适用场景、变体 grill-me-fix
  - 关联：[[claude-code]]、[[skill-system]]、[[hermes-subagent-orchestration]]、[[anthropic-prompting-best-practices]]
- 更新 index.md（total pages: 21 → 22, raw sources: 18 → 19）