---
title: "AI 技能 #04：API 测试器 — 你的本地 Postman"
date: 2026-03-29 11:18:00
tags:
  - AI
  - AI技能
  - API
  - HTTP
  - 调试
categories:
  - AI 开发
description: 给 AI 一个 URL 和参数，它就能帮你调接口、看响应、解释错误。不用打开 Postman。
---

# AI 技能 #04：API 测试器 — 你的本地 Postman

> 不用打开 Postman，直接说"调一下这个接口"就行。

## 这个技能能做什么？

- **调任意 HTTP 接口**：GET/POST/PUT/DELETE/PATCH 全支持
- **自动解析响应**：JSON/XML/HTML/CSV 自动识别
- **错误分析**：4xx/5xx 不是给你看状态码，是解释为什么错了
- **带认证**：Bearer Token、API Key、Basic Auth 全支持
- **文件上传**：multipart/form-data 也能搞

## 怎么用？

### GET 请求

```
"调一下 https://api.github.com/users/torvalds"
"看看 httpbin.org/get 返回什么"
```

### POST 请求

```
"POST https://api.example.com/login，Body 是 {\"user\":\"admin\",\"pass\":\"123\"}"
```

### 带认证

```
"用 token Bearer xxx 调 GET /api/v2/users?page=1"
"Header 带 X-API-Key: mykey，调一下 https://api.example.com/data"
```

### 复杂场景

```
"上传文件 D:\report.pdf 到 https://api.example.com/upload"
"调这个接口，如果有 429 就自动等 Retry-After 后重试"
```

## 异常处理

AI 不是报个状态码就完了：

| 状态码 | AI 会告诉你 |
|--------|------------|
| 400 | 参数哪里错了，正确格式是什么 |
| 401 | Token 缺失/过期，怎么重新获取 |
| 403 | 你没有这个权限，需要什么 scope |
| 404 | URL 对不对？资源 ID 存不存在？ |
| 429 | 等多少秒再试 |
| 500 | 服务端错误，建议联系后端 |

## 底层实现

- 简单请求：用 `curl`
- 复杂请求：生成 Python `requests` 临时脚本
- 响应截断：超过 5000 字符自动截断

---

*下一篇：[AI 技能 #05：数据分析 →](/my-blog/2026/03/29/skill-data-analyzer/)*
