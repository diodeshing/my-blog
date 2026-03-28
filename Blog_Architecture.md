# 博客架构文档

## 框架选择：Hexo

### 为什么选 Hexo
1. **Node.js 生态**：你已有 Node 24，无需额外安装运行时
2. **中文友好**：官方文档、社区、主题大多有中文支持
3. **主题丰富**：Butterfly、NexT、fluid 等高质量中文主题
4. **部署简单**：`hexo deploy` 一键推送到 GitHub Pages
5. **Markdown 原生**：文章直接用 .md 文件编写

### 备选方案对比
| 框架 | 语言 | 优点 | 缺点 |
|------|------|------|------|
| Hexo | Node.js | 中文生态好、主题多、上手快 | 构建速度中等 |
| Hugo | Go | 构建极快、单文件 | 模板语法复杂、中文主题少 |
| VitePress | Vue/Vite | 现代、速度快 | 更适合文档站、博客功能弱 |

## 目录结构

```
D:\MyBlog\
├── _config.yml          ← Hexo 主配置
├── package.json         ← Node 依赖
├── source/              ← 内容源
│   ├── _posts/          ← 博客文章（Markdown）
│   ├── about/           ← 关于页面
│   └── _drafts/         ← 草稿
├── themes/              ← 主题目录
│   └── butterfly/       ← Butterfly 主题（已配置）
├── scaffolds/           ← 文章模板
└── public/              ← 生成的静态文件（hexo g 后出现）
```

## 部署思路

### 方式一：GitHub Pages（推荐，免费）
1. 创建 GitHub 仓库 `diodeshing.github.io`
2. 安装 `hexo-deployer-git`
3. 配置 `_config.yml` 的 deploy 字段
4. 执行 `hexo clean && hexo generate && hexo deploy`

### 方式二：本地预览
```bash
hexo server    # 启动本地服务器 http://localhost:4000
hexo clean     # 清理缓存
hexo generate  # 生成静态文件
```

## 默认配置
- 主题：Butterfly（功能全面、中文支持好、响应式设计）
- 语言：zh-CN
- 时区：Asia/Shanghai
- 每页文章数：10
- Markdown 渲染器：hexo-renderer-marked
