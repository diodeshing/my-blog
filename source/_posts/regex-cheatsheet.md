---
title: "正则表达式速查：10 个最常用的模式"
date: 2026-03-28 20:30:00
tags:
  - 正则表达式
  - 编程
  - 速查
categories:
  - 编程技巧
description: 手机号、邮箱、IP 地址、URL 等 10 个最常用的正则表达式，复制即用。
---

# 正则表达式速查：10 个最常用的模式

正则不需要精通，记住 10 个常用模式就够日常用了。

## 基础语法速查

```
.       任意字符
\d      数字 [0-9]
\w      字母数字下划线 [a-zA-Z0-9_]
\s      空白字符
*       0 次或多次
+       1 次或多次
?       0 次或 1 次
{n,m}   n 到 m 次
^       开头
$       结尾
[]      字符集合
|       或
()      分组捕获
```

## 10 个常用模式

### 1. 手机号（中国大陆）
```regex
^1[3-9]\d{9}$
```
```python
import re
re.match(r'^1[3-9]\d{9}$', '13812345678')  # ✅
```

### 2. 邮箱
```regex
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```
```python
re.match(r'^[\w.+-]+@[\w-]+\.[\w.]+$', 'user@example.com')  # ✅
```

### 3. IP 地址
```regex
^(\d{1,3}\.){3}\d{1,3}$
```

### 4. URL
```regex
^https?://[^\s/$.?#].[^\s]*$
```

### 5. 日期（YYYY-MM-DD）
```regex
^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01])$
```

### 6. 中文字符
```regex
[\u4e00-\u9fa5]+
```
```python
re.findall(r'[\u4e00-\u9fa5]+', 'Hello你好World世界')
# ['你好', '世界']
```

### 7. 提取数字
```regex
\d+\.?\d*
```
```python
re.findall(r'\d+\.?\d*', '价格 ¥199.9 库存 42')
# ['199.9', '42']
```

### 8. 密码强度（至少 8 位，包含大小写和数字）
```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$
```

### 9. 去除首尾空白
```regex
^\s+|\s+$
```
```python
re.sub(r'^\s+|\s+$', '', '  hello  ')  # 'hello'
```

### 10. 提取 HTML 标签内容
```regex
<(\w+)[^>]*>(.*?)</\1>
```

## Python 实用函数

```python
import re

def match_phone(text):
    """提取文本中的手机号"""
    return re.findall(r'1[3-9]\d{9}', text)

def match_email(text):
    """提取文本中的邮箱"""
    return re.findall(r'[\w.+-]+@[\w-]+\.[\w.]+', text)

def replace_blank(text):
    """多个空格替换为一个"""
    return re.sub(r'\s+', ' ', text).strip()

# 使用
text = "联系人：张三 13812345678 zhang@example.com"
print(match_phone(text))  # ['13812345678']
print(match_email(text))  # ['zhang@example.com']
```

## 在线测试工具

- [regex101.com](https://regex101.com) — 最好用的在线正则测试
- [regexr.com](https://regexr.com) — 可视化解释

## 总结

> 正则表达式是"写一次，查一辈子"的东西。**不需要记住所有规则，只需要收藏这篇，用到时 Ctrl+F 查一下。**

---

*更多编程速查关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
