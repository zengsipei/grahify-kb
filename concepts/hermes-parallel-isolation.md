---
title: Hermes 并行隔离模式
created: 2026-05-09
updated: 2026-05-09
type: concept
tags: [agent, workflow, worktree, backend, isolation]
sources: [raw/articles/2026-05-05-claude-code-operator模式.md, raw/articles/2026-05-09-hermes-operator-pattern.md]
---

# Hermes 并行隔离模式

对比 Claude Code 的 Worktree 与 Hermes 的 `--worktree` + `--backend` 隔离策略。

## Claude Code

```bash
claude --worktree feature-auth    # git worktree + 独立 CLAUDE.md
```

## Hermes

```bash
hermes -w                                     # git worktree
hermes --backend ssh://server2                # SSH 远程
hermes --backend docker://gpu                 # Docker 容器
hermes --backend modal://worker               # 云端沙箱
```

## 关键差异

| 维度 | Claude Code | Hermes |
|------|------------|--------|
| 隔离级别 | git worktree（文件级） | 后端级（文件 + 环境 + 依赖） |
| 配置隔离 | 独立 CLAUDE.md | AGENTS.md / CLAUDE.md / .cursorrules |
| 远程执行 | ❌ | ✅ `--backend ssh://` |
| 容器化 | ❌ | ✅ `--backend docker://` |
| 云端沙箱 | ❌ | ✅ `--backend modal://` |
| 定时调度 | ❌ | ✅ `cron` 集成 |

## 适用场景

- **独立功能开发**：不同 worktree 并行开发不冲突
- **多环境验证**：同一任务在 Python 3.8/3.11/3.12 容器验证
- **GPU 任务隔离**：Docker 容器隔离 CUDA 环境
- **云端执行**：本地触发，云端 Modal 执行大模型任务

## 示例

```bash
# 本地开发 feature-auth
hermes -w feature-auth -q "Implement OAuth2 login"

# 同时在 Docker 中跑测试
hermes --backend docker://test-env -q "Run integration test suite"

# 定时在隔离环境跑 CI
hermes cron create "every 1h" "Run lint and tests"
```

## 相关页面

- [[hermes-agentic-workflows]] — 完整工作流模式概览
- [[hermes-subagent-orchestration]] — 子代理编排详解