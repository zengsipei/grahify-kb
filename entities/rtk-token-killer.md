---
title: rtk — Rust Token Killer
created: 2026-05-14
updated: 2026-05-23
type: entity
tags: [ai-tool, coding-assistant, rust, token-optimization, developer-tools, open-source]
sources: [raw/articles/2026-05-14-rtk-token-killer.md, raw/articles/2026-05-23-rtk-airtk-rust-token-killer.md]
confidence: high
---

# rtk — Rust Token Killer

**rtk** 是一个高性能 CLI 代理，拦截并压缩命令输出再送给 LLM，减少 token 消耗 60-90%。单个 Rust 二进制、零依赖、<10ms 开销。^[raw/articles/2026-05-14-rtk-token-killer.md]

## 核心数据（2026-05-14）

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 47,271 |
| 🍴 Forks | 2,862 |
| 🐛 Open Issues | 904 |
| 🦀 语言 | Rust |
| 📜 License | Apache-2.0 |
| 🏠 官网 | https://www.rtk-ai.app |
| 📅 创建 | 2026-01-22 |

## 工作原理

rtk 作为透明代理插在 LLM 和 shell 之间：

```
Without rtk:  LLM → shell → git → LLM（~2,000 tokens 原始输出）
With rtk:     LLM → rtk → git → rtk（过滤）→ LLM（~200 tokens 紧凑输出）
```

四大压缩策略：
1. **Smart Filtering** — 剻噪（注释、空行、样板代码）
2. **Grouping** — 聚合（按目录/类型归组文件、按规则归组 lint 错误）
3. **Truncation** — 截断冗余上下文
4. **Deduplication** — 折叠重复日志行并计数

## Token 节省估算（30 分钟 Claude Code 会话）

| 操作 | 原始 tokens | rtk 后 | 节省率 |
|------|------------|--------|--------|
| ls/tree | 2,000 | 400 | **80%** |
| cat/read | 40,000 | 12,000 | **70%** |
| grep/rg | 16,000 | 3,200 | **80%** |
| git status | 3,000 | 600 | **80%** |
| git add/commit/push | 1,600 | 120 | **92%** |
| cargo test | 25,000 | 2,500 | **90%** |
| pytest | 8,000 | 800 | **90%** |
| docker ps | 900 | 180 | **80%** |
| **总计** | **~118K** | **~24K** | **~80%** |

## 覆盖范围

100+ 命令，涵盖：
- **文件操作**：`ls`、`read`、`find`、`grep`、`diff`
- **Git 全套**：`status`、`log`、`diff`、`add`、`commit`、`push`、`pull`
- **GitHub CLI**：`gh pr list/view`、`gh issue list`、`gh run list`
- **测试框架**：Jest、Vitest、Playwright、pytest、cargo test、go test、rspec
- **构建/lint**：ESLint、tsc、cargo clippy、ruff、golangci-lint、rubocop
- **包管理**：pnpm、pip、bundle、prisma
- **基础设施**：AWS CLI、Docker、Kubernetes
- **数据/日志**：JSON、env、log、curl

## AI 编码工具集成

rtk 支持 13 种 AI 编码工具，通过 hook 或插件实现命令自动重写：

| 工具 | 接入方式 |
|------|---------|
| Claude Code | PreToolUse hook |
| GitHub Copilot | PreToolUse hook |
| Cursor | hooks.json |
| Gemini CLI | BeforeTool hook |
| Codex | AGENTS.md + RTK.md |
| [[Hermes]] | Python 插件（`rtk init --agent hermes`） |
| Windsurf | .windsurfrules |
| Cline / Roo Code | .clinerules |
| OpenCode | Plugin TS |

Hermes 集成使用 Python 插件适配器，通过 `rtk rewrite` 进行 terminal command mutation，与 [[hermes-agentic-workflows]] 中的代理工作流模式深度协同。^[raw/articles/2026-05-14-rtk-token-killer.md]

## 安装

```bash
brew install rtk                                          # Homebrew（推荐）
curl -fsSL https://raw.githubusercontent.com/rtk-ai/rtk/refs/heads/master/install.sh | sh  # 一键安装
cargo install --git https://github.com/rtk-ai/rtk         # Cargo
```

快速启动：
```bash
rtk init -g                     # Claude Code / Copilot（默认）
rtk init -g --agent hermes      # Hermes 集成
rtk gain                        # 查看 token 节省统计
```

## 与其他工具的关系

- [[obscura-browser]] — 同为 Rust 语言高性能工具，rtk 优化 token 流量而 obscura 优化浏览器自动化
- [[pretext]] — 同为极致性能导向的开发者工具，rtk 追求 <10ms 开销而 pretext 追求比 DOM 快 300-600x
- [[hermes-agentic-workflows]] — rtk 的 Hermes 插件深度融入代理编排工作流，减少整个 subagent 链路的 token 消耗

## 核心团队

- **Patrick Szymkowiak** — Founder ([GitHub](https://github.com/pszymkowiak))
- **Florian Bruniaux** — Core contributor ([GitHub](https://github.com/FlorianBruniaux))
- **Adrien Eppling** — Core contributor ([GitHub](https://github.com/aeppling))

## 隐私

遥测默认关闭，需显式 opt-in（GDPR Art. 6/7 合规）。收集匿名聚合数据，不收集源代码、文件路径、命令参数、密钥等敏感信息。