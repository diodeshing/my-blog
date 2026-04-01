---
title: "和AI协作的前五天：从零搭建到全栈修复"
date: 2026-04-01 19:30:00
tags:
  - AI
  - OpenClaw
  - 博客搭建
  - 开发日记
categories:
  - 技术分享
description: "记录从3月28日首次对话到4月1日博客大修复的五天，16个技能上线、37篇文章发布、一次完整的故障排查。"
sticky: 3
---

# 和AI协作的前五天：从零搭建到全栈修复

五天前，这个博客还不存在。五天后，37篇文章在线、16个技能就绪、GitHub Actions 自动部署。这段从零到一的过程，值得记录一下。

---

## Day 1 — 3月28日：一切从空白开始

### 第一次对话

下午5点47分，和 AI 智能体 OpenClaw 开始了第一次对话。设置了一些基本偏好：中文交流、ReAct 工作模式（先想再做）、双模态协议（学习模式 vs 应用模式）。

### 技能批量创建

用大模型（mimo-v2-pro）教本地小模型（qwen3.5:4b），一口气创建了 15 个基础技能：

- 代码助手、文本处理、数据分析
- 文件管理、网络研究、博客搭建
- 深度网页抓取、Notion+Obsidian 联动
- 数据库分析、自动化通知、天气查询……

**核心思路：** 强模型学技能 → 存成本地文件 → 小模型直接复用。第一次做要花时间，第二次就是秒级。

### 博客上线

框架选型（Hexo + Butterfly）→ 项目初始化 → GitHub Actions CI/CD → 部署上线。整个过程不到一小时。

一口气写了 10 篇技术博客：Python 技巧、终端美化、Markdown 速成、Git 规范、编程语言推荐、Docker 入门……

**博客名：** 击穿二极管 🔧

---

## Day 2 — 3月29日：技能扩展与批量发文

### 新增技能

- **Whisper 语音转文字** — 本地推理，无需联网，CPU 跑 base 模型约 12-17s/条
- **API 测试器** — 本地 Postman，用 curl 或 Python requests
- **Tesseract OCR** — 中英文识别，配合 PyMuPDF 处理 PDF

### 22 篇技能博客

创建了「AI技能」专栏，批量发布 22 篇技能介绍文章。每篇包含：功能描述、安装步骤、使用方式、测试口令。

### 测试报告

发布了一篇 18 个技能全测试报告，附 Ollama 本地模型配置指南。

---

## Day 3 — 3月30~31日：ARIS 研究项目

克隆了 ARIS（AI Research Agent System）仓库，开始探索 AI 辅助学术研究。

选定项目：**DynamicYOLO**（动态推理目标检测）。配置了 conda 环境（Python 3.9 + PyTorch 2.3 + RTX 3060），启动了 Phase 0 基线训练。

---

## Day 5 — 4月1日：博客大维修

### 发现问题

博客首页空白，`https://diodeshing.github.io/my-blog/` 无法访问。

### 排查过程（耗时较长）

这不是一个简单的问题，层层剥洋葱：

**第一层：文章内容截断**
- `daily-2026-03-28.md` 和 `hello-world.md` 内容被截断 60-80%
- 从 Git 历史恢复完整版本
- ⚠️ 教训：PowerShell 的 `Out-File` 会破坏中文编码，恢复文件必须用 `git checkout`

**第二层：Butterfly 主题模板崩溃**
- `config.pug` 模板中 `config.algolia` 未定义 → TypeError
- 这个错误导致**所有页面**渲染失败，index.html 输出 0 字节
- 重写 config.pug 绕过 Algolia 空值检查

**第三层：缺少依赖插件**
- `hexo-generator-searchdb` 未安装 → `config.search.path` undefined
- `hexo-wordcount` 未安装 → `totalcount(site)` 函数不存在
- 每个缺失都导致新的 TypeError

**第四层：GitHub Pages 被关闭**
- `has_pages: false` — Pages 功能被意外关闭
- 通过 API 重新开启并构建

### 修复成果

```bash
npm install hexo-generator-searchdb hexo-wordcount --save
```

- 恢复 2 篇被截断文章
- 创建 `_config.butterfly.yml` 自定义主题配置
- 修复侧边栏、公告栏、页脚年份
- 启用本地搜索、字数统计
- GitHub Pages 重新部署成功

---

## 五天数据

| 指标 | 数值 |
|------|------|
| 工作天数 | 5 天 |
| 博客文章 | 37 篇 |
| 技能数量 | 16 个 |
| 渠道配置 | WebChat ✅ 飞书 ✅ Email ✅ |
| 代码仓库 | 1 个（GitHub Pages 自动部署） |
| 研究项目 | 1 个（DynamicYOLO） |

---

## 收获与反思

1. **AI 不是替代者，是加速器** — 它负责执行，人类负责决策。五天的产出量相当于手动一个月。

2. **依赖管理很重要** — Butterfly 主题对 npm 依赖非常敏感，缺失一个包就会导致整个站点空白。`package.json` 必须声明所有依赖。

3. **调试要逐层排除** — 这次博客修复经历了四层问题（内容截断 → 模板崩溃 → 缺依赖 → Pages 关闭），每一层都掩盖了下一层。

4. **Git 是最好的备份** — 两篇丢失的文章靠 Git 历史恢复了。没有 Git 历史就真的丢了。

5. **自动化部署的双刃剑** — GitHub Actions 自动部署很方便，但一旦配置出问题，排查链路变长（本地构建 vs 远程构建的差异）。

---

## 下一步

- 继续 DynamicYOLO 实验（Phase 1 动态推理）
- 博客添加评论系统（Giscus）
- 探索更多 ClawHub 技能
- 配置 Telegram Bot 推送

---

*这是第 38 篇。继续更新。*

---

*博客地址：[击穿二极管](https://diodeshing.github.io/my-blog/) | GitHub：[diodeshing](https://github.com/diodeshing)*
