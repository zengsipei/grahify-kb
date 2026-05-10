---
title: Hermes Cron 流水线
created: 2026-05-09
updated: 2026-05-09
type: concept
tags: [agent, workflow, cron, headless, automation]
sources: [raw/articles/2026-05-05-claude-code-operator模式.md, raw/articles/2026-05-09-hermes-operator-pattern.md]
---

# Hermes Cron 流水线

Hermes 对 Claude Code Headless 模式的根本性扩展——从单次执行升级为**持久化编排流水线**。

## Claude Code Headless

```bash
claude -p "Find and fix lint errors" --allowedTools "Read,Edit,Bash"
```

单次执行，无持久化，无编排。

## Hermes Cron

```bash
# 单次定时
hermes cron create "0 6 * * *" "每日市场分析"

# 链式流水线
hermes cron create "every 30m" "采集数据"        # job A
hermes cron create "every 2h" "分析" \
  --context_from=A_ID                            # job B 引用 A
hermes cron create "every 6h" "生成报告" \
  --context_from=B_ID                            # job C 引用 B
```

## 关键能力

| 能力 | Claude Code | Hermes |
|------|------------|--------|
| 持久化 | ❌ | ✅ SQLite 存储 |
| 链式依赖 | ❌ | ✅ `--context_from` |
| 多平台推送 | ❌ | ✅ weixin/telegram/discord/slack/email |
| 纯脚本模式 | ❌ | ✅ `--no-agent` |
| 多后端执行 | ❌ | ✅ `--backend` |
| 智能通知 | ❌ | ✅ `watch_patterns` / `notify_on_complete` |

## 模式对比

```
Claude Code Headless:
  单次触发 → 执行 → 输出到 stdout → 退出

Hermes Cron Pipeline:
  job A (采集) → job B (分析) → job C (报告)
       ↓              ↓              ↓
   web scraping   delegate_task   send_message
   every 30m      context_from=A  deliver=weixin
```

## 使用场景

- **定时数据采集**：每 30 分钟爬取市场数据
- **自动分析**：每 2 小时分析数据变化
- **报告推送**：每 6 小时生成并推送报告到微信
- **CI/CD 集成**：代码提交后自动跑测试
- **监控告警**：服务异常时自动通知

## 示例

```bash
# 监控任务
hermes cron create "every 5m" \
  --script "check_service.sh" \
  --watch_patterns "ERROR" \
  --deliver telegram

# 纯脚本 watchdog（无 LLM）
hermes cron create "every 1h" \
  --no-agent \
  --script "watchdog.py"
```

## 相关页面

- [[hermes-agentic-workflows]] — 完整工作流模式概览
- [[hermes-kanban-orchestrator]] — Kanban 编排详解