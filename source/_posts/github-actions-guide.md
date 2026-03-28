---
title: "为什么你应该用 GitHub Actions 做 CI/CD"
date: 2026-03-28 20:27:00
tags:
  - GitHub Actions
  - CI/CD
  - 自动化
categories:
  - 工具推荐
description: GitHub Actions 免费、简单、和 GitHub 无缝集成，是个人项目和小团队的最佳 CI/CD 方案。
---

# 为什么你应该用 GitHub Actions 做 CI/CD

Jenkins 太重，GitLab CI 需要自建，Travis CI 免费额度少。**GitHub Actions 免费、开箱即用。**

## 什么是 CI/CD

```
CI（持续集成）= 每次提交代码，自动测试
CD（持续部署）= 测试通过，自动发布
```

简单说：**推代码 → 自动测试 → 自动部署**。你不用手动操作。

## GitHub Actions 免费额度

| 资源 | 免费额度 |
|------|---------|
| 公开仓库 | **无限** |
| 私有仓库 | 2000 分钟/月 |
| 存储 | 500 MB |

个人项目完全够用。

## 最简示例

创建 `.github/workflows/hello.yml`：

```yaml
name: Hello CI

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 22
      - run: npm ci
      - run: npm test
```

推送到 main 分支，GitHub 自动运行测试。

## 实用场景

### 1. 代码检查
```yaml
- name: Lint
  run: npx eslint .
```

### 2. 自动部署到服务器
```yaml
- name: Deploy
  uses: appleboy/ssh-action@v1
  with:
    host: ${{ secrets.SERVER_HOST }}
    username: ${{ secrets.SERVER_USER }}
    key: ${{ secrets.SSH_KEY }}
    script: cd /app && git pull && npm install && pm2 restart all
```

### 3. 定时任务
```yaml
on:
  schedule:
    - cron: '0 9 * * 1'  # 每周一早上9点
```

## Secrets 管理

敏感信息不要写在 YAML 里：
1. 仓库 → Settings → Secrets → Actions
2. 添加 `DEPLOY_KEY`、`API_TOKEN` 等
3. 代码里用 `${{ secrets.DEPLOY_KEY }}` 引用

## 常用 Actions

| Action | 用途 |
|--------|------|
| `actions/checkout` | 检出代码 |
| `actions/setup-node` | 安装 Node.js |
| `actions/setup-python` | 安装 Python |
| `peaceiris/actions-gh-pages` | 部署到 GitHub Pages |
| `docker/build-push-action` | 构建并推送 Docker 镜像 |

## 总结

> 如果你的项目在 GitHub 上，就**没有理由不用 GitHub Actions**。免费、简单、和代码仓库在一起，不需要额外维护任何东西。

---

*更多自动化技巧关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
