---
title: "AI 技能 #08：Whisper 语音转文字 — 本地运行，不联网"
date: 2026-03-29 11:22:00
tags:
  - AI
  - AI技能
  - 语音识别
  - Whisper
  - 音频
categories:
  - AI 开发
description: 用 OpenAI 的 Whisper 模型在本地将音频转为文字，支持 mp3/wav/m4a 等格式，可生成 SRT 字幕。
---

# AI 技能 #08：Whisper 语音转文字 — 本地运行，不联网

> 会议录音、播客、网课音频，扔进来就变文字。

## 这个技能能做什么？

- **音频转文字**：mp3/wav/m4a/flac/ogg/mp4 全支持
- **语言自动检测**：中/英/日/韩自动识别
- **生成字幕**：输出 SRT/VTT 字幕文件
- **时间戳**：每段话都有起止时间
- **完全离线**：不需要联网，不调 API

## 怎么用？

### 基础转录

```
"转录这个音频: D:\audio\meeting.mp3"
→ 输出: D:\audio\meeting.txt
```

### 指定模型和语言

```
"把 voice.wav 转成文字，用 small 模型，中文"
```

### 生成字幕

```
"帮我把 podcast.m4a 转成 SRT 字幕"
```

## 模型选择

| 模型 | 大小 | 速度 | 推荐场景 |
|------|------|------|----------|
| tiny | 72MB | 极快 | 快速测试 |
| **base** | 139MB | 快 | **日常使用** |
| small | 466MB | 中等 | 精度优先 |
| medium | 1.5GB | 较慢 | 高精度 |
| large | 2.9GB | 慢 | 最高精度 |

## 技术架构

```
音频 → ffmpeg 解码 → Whisper 推理 → 文本/字幕
```

基于 OpenAI 开源的 Whisper 模型，本地推理，数据不离开电脑。

## 支持格式

mp3 ✅ wav ✅ m4a ✅ ogg ✅ flac ✅ mp4 ✅ webm ✅ aac ✅

---

*下一篇：[AI 技能 #09：网页抓取 →](/my-blog/2026/03/29/skill-deep-web-scraper/)*
