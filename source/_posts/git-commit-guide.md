---
title: "Git 提交信息写法指南：告别 'fix bug' 和 'update'"
date: 2026-03-28 20:24:00
tags:
  - Git
  - 规范
  - 效率
categories:
  - 编程技巧
description: 一套简单实用的 Git commit 规范，让提交历史清晰可读，方便回溯和协作。
---

# Git 提交信息写法指南：告别 "fix bug" 和 "update"

你的 Git 提交记录是不是这样的？

```
fix
update
修改
bug
改了点东西
```

看一眼就头疼。来学一套简单的规范。

## 格式

```
<类型>: <简短描述>

<可选的详细说明>
```

## 类型速查

| 类型 | 用途 | 示例 |
|------|------|------|
| `feat` | 新功能 | `feat: 添加用户登录功能` |
| `fix` | 修复 bug | `fix: 修复空指针异常` |
| `docs` | 文档更新 | `docs: 更新 README 安装说明` |
| `style` | 格式调整（不影响逻辑） | `style: 统一缩进为 2 空格` |
| `refactor` | 重构（无功能变化） | `refactor: 拆分 utils 模块` |
| `perf` | 性能优化 | `perf: 优化查询缓存逻辑` |
| `test` | 测试相关 | `test: 添加登录接口单元测试` |
| `chore` | 构建/工具变更 | `chore: 升级 webpack 到 v5` |

## 实例对比

**❌ 垃圾提交：**
```bash
git commit -m "fix bug"
git commit -m "修改代码"
git commit -m "update"
```

**✅ 清晰提交：**
```bash
git commit -m "fix: 修复登录时密码未加密的问题"
git commit -m "feat: 添加用户头像上传功能"
git commit -m "refactor: 将数据库连接逻辑抽取为独立模块"
```

## 带详细说明

```bash
git commit -m "feat: 添加搜索功能

- 支持关键词模糊搜索
- 支持按分类筛选
- 搜索结果分页展示

Closes #42"
```

## 小技巧

```bash
# 查看提交历史（简洁版）
git log --oneline

# 查看某文件的修改历史
git log --oneline -- path/to/file.js

# 撤销上一次提交（保留修改）
git commit --amend
```

## 团队协作

如果项目没有规范，提一个 PR 引入 [Conventional Commits](https://www.conventionalcommits.org/)。只需要 5 分钟培训，整个团队的代码历史就会变得清晰。

## 总结

> 提交信息不是写给自己的，是写给**三个月后调试 bug 的你**和**协作的队友**的。多写 5 个字，少查 30 分钟日志。

---

*更多编程规范关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
