---
title: "Docker 入门：3 条命令搞定本地开发环境"
date: 2026-03-28 20:26:00
tags:
  - Docker
  - 开发环境
  - 容器
categories:
  - 技术分享
description: 用最简单的 Docker 命令，在任何电脑上还原一模一样的开发环境。
---

# Docker 入门：3 条命令搞定本地开发环境

"我电脑上跑得好好的啊？" —— 每个开发者都说过这句话。Docker 就是解决这个问题的。

## 核心概念

```
镜像（Image）= 软件安装包
容器（Container）= 运行中的软件实例
Dockerfile = 安装说明书
```

## 3 条核心命令

### 1. 拉取镜像
```bash
docker pull python:3.12
docker pull node:22
docker pull postgres:16
```

### 2. 运行容器
```bash
# 启动一个 Python 环境
docker run -it python:3.12 python

# 启动 PostgreSQL 数据库
docker run -d --name mydb \
  -e POSTGRES_PASSWORD=123456 \
  -p 5432:5432 \
  postgres:16
```

### 3. 管理容器
```bash
docker ps          # 查看运行中的容器
docker stop mydb   # 停止
docker rm mydb     # 删除
docker logs mydb   # 查看日志
```

## 实战：一键启动开发环境

创建 `docker-compose.yml`：

```yaml
version: "3.8"

services:
  # 数据库
  postgres:
    image: postgres:16
    environment:
      POSTGRES_DB: myapp
      POSTGRES_PASSWORD: dev123
    ports:
      - "5432:5432"

  # 缓存
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"

  # 你的应用
  app:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - postgres
      - redis
    volumes:
      - .:/app
```

启动整个环境：
```bash
docker compose up -d
```

一行命令，数据库 + 缓存 + 应用全部启动。

## Dockerfile 示例

```dockerfile
FROM node:22-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

## 常用技巧

```bash
# 清理无用镜像（释放空间）
docker system prune -a

# 进入运行中的容器
docker exec -it mydb bash

# 查看容器资源占用
docker stats
```

## 总结

> Docker 解决的核心问题不是"容器化"，而是**"在我电脑上能跑"**。花 30 分钟学会 3 条命令，以后换电脑、换环境、换队友都不怕。

---

*更多 DevOps 技巧关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
