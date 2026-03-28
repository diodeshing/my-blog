---
title: Hello World：我的 AI 助手帮我搭建了这个博客
date: 2026-03-28 19:55:00
sticky: 1
tags:
  - Hexo
  - AI
  - 博客搭建
categories:
  - 技术分享
description: 记录用 AI 助手搭建 Hexo 博客的全过程，从框架选型到自动部署。
---

# Hello World：我的 AI 助手帮我搭建了这个博客

这是我写的第一篇博客。和大多数 "Hello World" 不同，**这个博客本身就是一个 Hello World** —— 整个搭建过程，从框架选型到自动部署，都是我和 AI 助手协作完成的。

## 为什么要做这个博客

我一直想有一个自己的技术博客，但每次都被以下问题劝退：

- **选框架**：Hexo、Hugo、VitePress、Jekyll……选择太多，反而不知道选哪个
- **配环境**：Node.js 版本、依赖冲突、主题配置……光环境就折腾半天
- **部署**：GitHub Pages、Vercel、Netlify……流程不熟悉

这次我决定换个思路 —— **让 AI 来做**。我只负责提需求，剩下的交给它。

## 框架选型：为什么选 Hexo

经过 AI 的分析，最终选择了 **Hexo**，原因很简单：

| 对比项 | Hexo | Hugo | VitePress |
|--------|------|------|-----------|
| 语言 | Node.js | Go | Vue/Vite |
| 上手难度 | ⭐ 低 | ⭐⭐ 中 | ⭐⭐ 中 |
| 中文主题 | 非常丰富 | 较少 | 少 |
| 适合场景 | 个人博客 | 文档站 | 技术文档 |

Hexo 最大的优势是 **中文生态好** —— Butterfly、NexT 等主题质量很高，社区活跃。

## 搭建过程

整个过程分四步，每步都由 AI 执行：

### 1. 创建项目结构

```bash
# AI 生成了完整的目录结构
D:\MyBlog\
├── _config.yml          # 主配置
├── package.json         # 依赖管理
├── source/_posts/       # 文章目录
├── source/about/        # 关于页面
└── scaffolds/           # 文章模板
```

### 2. 配置主题

选择了 **Butterfly** 主题 —— 响应式设计、支持暗色模式、功能丰富。

### 3. 设置自动部署

配置了 GitHub Actions，每次推送到 main 分支就自动构建部署：

```yaml
# .github/workflows/deploy.yml
on:
  push:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
      - run: npm ci
      - run: npx hexo generate
      - uses: peaceiris/actions-gh-pages@v4
```

### 4. 测试与发布

```bash
# 本地预览
hexo server  # → http://localhost:4000

# 推送部署
git push origin main  # → GitHub Actions 自动构建
```

## 写作体验

用 Markdown 写博客非常舒服。只需要一个 `.md` 文件：

```markdown
---
title: 我的文章
date: 2026-03-28
tags: [技术]
---

这里是正文，支持所有 Markdown 语法。
```

## 未来计划

这个博客打算持续更新以下内容：

- **AI 开发实践**：大语言模型应用、智能体开发
- **编程技巧**：前端、后端、工具链
- **开源探索**：好用的开源项目推荐
- **效率工具**：开发环境配置、生产力提升

## 总结

从零到上线，整个过程不到一小时。AI 不仅帮我做了技术决策，还帮我写了这篇文章。

> 技术的进步不是让人类失业，而是让人类可以把时间花在更重要的事情上。

这是第一篇，期待后面更多内容。🚀

---

*如果这篇文章对你有帮助，欢迎 Star 我的 [GitHub](https://github.com/diodeshing)。*
