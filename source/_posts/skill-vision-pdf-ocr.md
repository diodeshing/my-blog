---
title: "AI 技能 #07：PDF & OCR — 让 AI 读懂 PDF 和图片"
date: 2026-03-29 11:21:00
tags:
  - AI
  - AI技能
  - PDF
  - OCR
  - 文字识别
categories:
  - AI 开发
description: 本地解析 PDF 文字和表格，OCR 识别图片/扫描件中的文字。支持中英文，无需上传云端。
---

# AI 技能 #07：PDF & OCR — 让 AI 读懂 PDF 和图片

> 不是上传到某云识别，是本地跑，数据不出电脑。

## 这个技能能做什么？

- **PDF 文字提取**：从 PDF 中提取所有文字
- **PDF 表格提取**：识别并导出表格数据
- **PDF 图片提取**：导出 PDF 中的图片
- **OCR 图片**：识别图片中的文字（中英文）
- **OCR 扫描件**：扫描版 PDF 转可搜索文本

## 怎么用？

```
"帮我读取 D:\docs\report.pdf 的内容"
"提取这个 PDF 里的表格数据"
"OCR 这张截图 D:\screenshot.png"
"这个扫描件 PDF 帮我转成文字"
```

## 技术栈

| 组件 | 作用 |
|------|------|
| PyMuPDF | PDF 文字/图片提取 |
| pdfplumber | PDF 表格提取 |
| Tesseract OCR | 文字识别引擎 |
| Pillow | 图片处理 |

## 支持格式

- PDF：文字版 ✅ 扫描版 ✅
- 图片：PNG ✅ JPG ✅ BMP ✅ TIFF ✅
- 语言：中文简体 ✅ 英文 ✅

## 本地运行

所有处理在本地完成，不需要联网，数据不离开你的电脑。适合处理敏感文档。

---

*下一篇：[AI 技能 #08：Whisper 语音转文字 →](/my-blog/2026/03/29/skill-whisper-transcriber/)*
