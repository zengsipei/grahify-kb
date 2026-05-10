---
title: Obscura
created: 2026-05-08
updated: 2026-05-08
type: entity
tags: [tool, browser, rust, headless, ai-agent, crawler, stealth]
sources: [raw/articles/2026-05-05-obscura-browser.md]
confidence: high
---

# Obscura

**Obscura** 是用 Rust 编写的开源无头浏览器引擎，专为 AI Agent 自动化和大规模网页爬取设计。

## 概述

- **语言**: Rust
- **JS 引擎**: V8
- **协议**: Chrome DevTools Protocol (CDP)
- **许可证**: Apache 2.0
- **平台**: Linux (x86_64), macOS (Apple Silicon/Intel), Windows

## 性能对比（vs Headless Chrome）

| 指标 | Obscura | Headless Chrome |
|------|---------|-----------------|
| 内存占用 | **30 MB** | 200+ MB |
| 二进制大小 | **70 MB** | 300+ MB |
| 页面加载 | **51-85 ms** | ~500 ms |
| 启动时间 | **即时** | ~2s |
| 反检测 | **内置 stealth 模式** | 无 |

## 核心功能

### Stealth 反检测模式

- 会话级指纹随机化（GPU、屏幕、画布、音频、电池）
- 真实 UserAgent（Chrome 145 高熵值）
- `event.isTrusted = true` 事件伪装
- `Function.prototype.toString()` → `[native code]` 原生函数伪装
- 3,520 个追踪域名屏蔽

### CLI 命令

```bash
obscura fetch <URL> --dump html          # 获取渲染后页面
obscura screenshot <URL>                  # 截图
obscura script <URL> --script <js>       # 执行 JS
```

## 适用场景

- **AI Agent 浏览器自动化** — 低资源占用，可并发多个实例
- **大规模网页爬取** — stealth 模式绕过反爬
- **端到端测试** — 轻量替代 Puppeteer/Playwright

## 相关页面

- [[browser-harness]] — 另一个浏览器自动化框架（Python + 自愈机制）
- [[hermes-agentic-workflows]] — Hermes 可通过 browser tool 调用 Obscura