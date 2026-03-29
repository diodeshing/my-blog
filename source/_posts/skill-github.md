---
title: "AI 技能 #02：GitHub 操作 — 用自然语言管仓库"
date: 2026-03-29 11:16:00
tags:
  - AI
  - AI技能
  - GitHub
  - DevOps
categories:
  - AI 开发
description: 无需记 git 命令，用大白话操作 GitHub。查 Issue、开 PR、跑 CI、看状态，全部语音化。
---

# AI 技能 #02：GitHub 操作 — 用自然语言管仓库

> "帮我看看 main 分支最近 5 个 commit" 比 `git log --oneline -5` 好记多了。

## 这个技能能做什么？

- **Issue 管理**：查看、创建、关闭 Issue
- **PR 操作**：创建 PR、查看差异、合并代码
- **CI/CD**：查看工作流状态、触发部署
- **仓库操作**：查看 commit、分支、标签
- **代码搜索**：跨仓库搜索代码片段

## 怎么用？

### Issue 操作

```
"看看这个仓库有什么 open issues"
"创建一个 Issue：标题是 xxx，描述是 yyy"
"关闭 issue #42"
"给 issue 打上 bug 标签"
```

### PR 操作

```
"看看 open 的 PR 有哪些"
"创建一个 PR 从 feature 分支到 main"
"查看 PR #15 的 diff"
"合并 PR #15"
```

### CI/CD

```
"最近的 CI 跑过了吗？"
"触发一下部署"
"看看哪个 workflow 失败了"
```

### 仓库状态

```
"最近 10 个 commit 是什么"
"看看有哪些分支"
"main 分支比 dev 落后几个 commit"
```

## 底层工具

此技能基于 GitHub CLI (`gh`)，AI 自动将你的自然语言翻译为 `gh` 命令。

## 注意事项

- 需要先配置 `gh auth login`
- 私有仓库需要相应权限
- 危险操作（force push、删除分支）会先确认

---

*下一篇：[AI 技能 #03：终端执行器 →](/my-blog/2026/03/29/skill-terminal-executor/)*
