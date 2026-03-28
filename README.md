# 击穿二极管 🔌

> 探索 AI 与编程的无限可能

基于 [Hexo](https://hexo.io/) + [Butterfly](https://github.com/jerryc127/hexo-theme-butterfly) 主题搭建的个人技术博客，部署在 GitHub Pages。

🔗 访问地址：**https://diodeshing.github.io/my-blog/**

## 这个项目怎么来的

这个博客是**和 AI 智能体协作完成的**，从零到上线大约 1 小时：

1. **框架选型** — AI 对比了 Hexo / Hugo / VitePress，选择了 Hexo（中文生态好、上手简单）
2. **项目初始化** — AI 自动生成了全部配置文件、目录结构和模板
3. **GitHub Actions** — AI 配置了自动部署流程，推送到 main 分支即自动构建上线
4. **内容创作** — 博客文章由 AI 协助撰写，涵盖编程技巧、工具推荐、AI 开发等方向

整个过程中，人类负责定方向和做决策，AI 负责执行和文档化。

## 博客内容

- 🐍 Python 编程技巧
- 🤖 AI 开发实践
- 🛠 效率工具推荐
- 📝 技术写作与规范
- 🔧 开发环境配置

## 本地运行

```bash
# 克隆仓库
git clone https://github.com/diodeshing/my-blog.git
cd my-blog

# 安装依赖
npm install

# 本地预览
npx hexo server
# 访问 http://localhost:4000

# 生成静态文件
npx hexo generate
```

## 写新文章

```bash
npx hexo new "文章标题"
# 编辑 source/_posts/文章标题.md
# git add + commit + push → 自动部署
```

## 技术栈

| 组件 | 技术 |
|------|------|
| 静态博客框架 | [Hexo](https://hexo.io/) 7.x |
| 主题 | [Butterfly](https://github.com/jerryc127/hexo-theme-butterfly) 5.x |
| 自动部署 | GitHub Actions |
| 托管 | GitHub Pages |
| AI 协作 | [OpenClaw](https://github.com/openclaw/openclaw) |

## 自动部署

每次推送到 `main` 分支，GitHub Actions 会自动：
1. 安装依赖
2. 生成静态文件
3. 部署到 `gh-pages` 分支

无需手动操作。

## License

MIT
