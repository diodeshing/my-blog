---
title: "REST API 设计规范：6 个让接口好用的原则"
date: 2026-03-28 20:28:00
tags:
  - API
  - REST
  - 后端
categories:
  - 编程技巧
description: 从 URL 命名到错误处理，6 个 REST API 设计的核心原则，写出前后端都喜欢的接口。
---

# REST API 设计规范：6 个让接口好用的原则

你的 API 是给前端同事用的，不是给你自己用的。设计得好，前端少写 bug，后端少接电话。

## 1. URL 用名词，用 HTTP 方法表示操作

**❌ 反面教材：**
```
GET  /getUser
POST /createUser
POST /deleteUser
GET  /updateUser
```

**✅ 正确写法：**
```
GET    /users         # 获取列表
GET    /users/42      # 获取单个
POST   /users         # 创建
PUT    /users/42      # 更新
DELETE /users/42      # 删除
```

## 2. 版本放在 URL 里

```
/v1/users
/v2/users
```

比 Header 版本控制更直观，出问题好排查。

## 3. 统一响应格式

```json
// 成功
{
  "code": 0,
  "data": { "id": 1, "name": "张三" },
  "message": "success"
}

// 失败
{
  "code": 40001,
  "data": null,
  "message": "用户名已存在"
}
```

**原则：** 结构永远一致，前端不用猜。

## 4. 分页和过滤

```
GET /users?page=2&size=20&sort=-created_at&status=active
```

```json
{
  "data": [...],
  "pagination": {
    "page": 2,
    "size": 20,
    "total": 156,
    "pages": 8
  }
}
```

## 5. 错误处理要具体

**❌ 模糊错误：**
```json
{ "code": 500, "message": "Internal Server Error" }
```

**✅ 具体错误：**
```json
{
  "code": 40001,
  "message": "用户名已被注册",
  "field": "username",
  "suggestion": "请尝试其他用户名"
}
```

## 6. 用状态码表达结果

| 状态码 | 含义 |
|--------|------|
| 200 | 成功 |
| 201 | 创建成功 |
| 400 | 参数错误 |
| 401 | 未认证 |
| 403 | 无权限 |
| 404 | 资源不存在 |
| 422 | 业务错误 |
| 429 | 请求太频繁 |
| 500 | 服务器错误 |

## 快速模板

```javascript
// Express.js 示例
app.get('/api/v1/users', async (req, res) => {
  const { page = 1, size = 20 } = req.query;
  const users = await User.find()
    .skip((page - 1) * size)
    .limit(size);

  res.json({
    code: 0,
    data: users,
    message: "success"
  });
});
```

## 总结

> 好的 API 设计就一句话：**前端拿到响应就知道该怎么做，不用打电话问后端。**

---

*更多后端设计关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
