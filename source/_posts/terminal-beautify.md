---
title: "终端美化指南：让你的命令行好看 10 倍"
date: 2026-03-28 20:22:00
tags:
  - 终端
  - 工具
  - 效率
categories:
  - 工具推荐
description: 从 Oh My Zsh 到 Starship 主题，手把手配置一个好看又好用的终端环境。
---

# 终端美化指南：让你的命令行好看 10 倍

默认终端又丑又难用。花 10 分钟配置一下，体验完全不同。

## 核心组件

```
终端模拟器（Windows Terminal / iTerm2）
  └── Shell（Zsh / PowerShell）
       └── 主题引擎（Starship / Oh My Zsh）
            └── 插件（自动补全、语法高亮、git 状态）
```

## Windows 方案

### 1. 安装 Windows Terminal
```powershell
winget install Microsoft.WindowsTerminal
```

### 2. 安装 Nerd Font
推荐 **CaskaydiaCove Nerd Font**：
```powershell
# 用 scoop 安装
scoop install CascadiaCode-NF
```
然后在 Windows Terminal 设置里把字体改成 `CaskaydiaCove NF`。

### 3. 安装 Starship（跨平台主题）
```powershell
winget install Starship.Starship
```

在 PowerShell 配置文件末尾加一行：
```powershell
# 编辑 $PROFILE
notepad $PROFILE

# 添加：
Invoke-Expression (&starship init powershell)
```

### 4. Starship 配置
创建 `~/.config/starship.toml`：
```toml
[character]
success_symbol = "[➜](bold green)"
error_symbol = "[✗](bold red)"

[python]
symbol = "🐍 "

[nodejs]
symbol = "⬢ "

[git_branch]
symbol = " "

[git_status]
ahead = "⇡${count}"
behind = "⇣${count}"
```

## macOS/Linux 方案

### 1. 安装 Oh My Zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 2. 安装插件
```bash
# 自动补全
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# 语法高亮
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

编辑 `~/.zshrc`，修改插件行：
```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

## 实用终端工具

| 工具 | 作用 | 安装 |
|------|------|------|
| `bat` | 带语法高亮的 cat | `winget install sharkdp.bat` |
| `eza` | 带图标的 ls | `scoop install eza` |
| `fzf` | 模糊搜索 | `winget install junegunn.fzf` |
| `zoxide` | 智能 cd | `winget install ajeetdsouza.zoxide` |
| `tldr` | 简洁命令手册 | `npm install -g tldr` |

## 配置前后对比

**配置前：**
```
C:\Users\diodeshing> dir
```

**配置后：**
```
➜  my-project ls
  src/  package.json  README.md
  main ← on  main  ✓  2 files changed
  🐍 3.12  ⬢ 22.0
```

## 总结

> 工具好不好看不重要，重要的是**看起来让你想用它**。终端美化不只是面子工程，git 状态显示、路径补全这些功能真的能提升效率。

---

*更多效率工具关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
