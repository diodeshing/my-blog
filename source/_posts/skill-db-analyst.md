---
title: "AI 技能 #06：数据库分析 — 自然语言查数据库"
date: 2026-03-29 11:20:00
tags:
  - AI
  - AI技能
  - 数据库
  - SQL
categories:
  - AI 开发
description: 连接 SQLite/MySQL/PostgreSQL，用中文问数据问题，AI 自动生成 SQL 并返回结果。
---

# AI 技能 #06：数据库分析 — 自然语言查数据库

> "上个月的订单总额是多少？" 比写 SQL 简单多了。

## 这个技能能做什么？

- **直连数据库**：SQLite、MySQL、PostgreSQL
- **自然语言查询**：说人话，AI 写 SQL
- **数据统计**：聚合、分组、排序、趋势
- **导出 CSV**：查询结果直接导出
- **表结构分析**：告诉你数据库里有什么

## 怎么用？

### SQLite

```
"查看 D:\data\app.db 有哪些表"
"统计 users 表里每个月注册了多少人"
"把 orders 表导出为 CSV"
```

### MySQL / PostgreSQL

先配置连接信息，然后：

```
"连上数据库，看看有哪些表"
"查询最近 7 天的销售额"
"哪个产品卖得最好？"
```

## 输出

AI 会给你：
1. **生成的 SQL**：让你知道它跑了什么
2. **查询结果**：格式化的表格
3. **数据洞察**：用中文解释结果含义

## 安全

- 默认只读（SELECT）
- 写操作（INSERT/UPDATE/DELETE）需要确认
- 不会碰系统表

---

*下一篇：[AI 技能 #07：PDF & OCR →](/my-blog/2026/03/29/skill-vision-pdf-ocr/)*
