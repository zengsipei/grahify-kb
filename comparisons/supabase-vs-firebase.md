---
title: Supabase vs Firebase
created: 2026-05-09
updated: 2026-05-09
type: comparison
tags: [comparison, database, backend]
sources: [raw/articles/2026-05-07-supabase-firebase.md]
---

# Supabase vs Firebase 对比

开源 Postgres 后端 vs Google 全托管 BaaS。

## 核心对比

| 维度 | Supabase | Firebase |
|------|----------|----------|
| **数据库** | PostgreSQL | Firestore (NoSQL) |
| **开源** | ✅ 完全开源 | ❌ Google 专有 |
| **自托管** | ✅ 可以 | ❌ 不可以 |
| **实时** | ✅ 原生支持 | ✅ 原生支持 |
| **Auth** | ✅ 内置 | ✅ 内置 |
| **存储** | ✅ 内置 | ✅ 内置 |
| **边缘函数** | ✅ Edge Functions | ✅ Cloud Functions |
| **定价** | 按用量， generous free tier | 按用量， generous free tier |
| **生态** | 较小但增长快 | Google 生态 |

## 选择建议

| 场景 | 推荐 |
|------|------|
| 需要 SQL/关系型数据 | **Supabase** |
| 需要 NoSQL/文档型数据 | **Firebase** |
| 需要自托管/数据主权 | **Supabase** |
| 深度集成 Google 服务 | **Firebase** |
| 团队熟悉 PostgreSQL | **Supabase** |
| 快速原型，无运维负担 | 两者皆可 |

## 关键差异

### Supabase 优势
- **开源透明**：可以审计代码，自托管
- **SQL 强大**：PostgreSQL 的完整能力
- **数据主权**：数据在你控制的服务器上
- **扩展性**：PostgreSQL 生态丰富

### Firebase 优势
- **Google 背书**：稳定性、全球基础设施
- **生态整合**：与 GCP、Google Analytics 深度集成
- **NoSQL 灵活**：适合非结构化数据
- **成熟度高**：运行多年，文档丰富

## 相关页面

- [[hermes-agentic-workflows]] — 后端选型决策流程