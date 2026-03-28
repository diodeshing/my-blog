---
title: "5 个让你少写 80% 代码的 Python 技巧"
date: 2026-03-28 20:21:00
tags:
  - Python
  - 编程技巧
  - 效率
categories:
  - 编程技巧
description: 列表推导、上下文管理器、海象运算符等 5 个 Python 高效写法，告别冗余代码。
---

# 5 个让你少写 80% 代码的 Python 技巧

很多人写 Python 的方式还停留在"翻译 Java"的阶段。其实 Python 有很多语法糖，能让你的代码短一半还更清晰。

## 1. 列表推导式

**❌ 笨拙写法：**
```python
result = []
for x in range(10):
    if x % 2 == 0:
        result.append(x ** 2)
```

**✅ 一行搞定：**
```python
result = [x ** 2 for x in range(10) if x % 2 == 0]
# [0, 4, 16, 36, 64]
```

字典推导也一样：
```python
word_lengths = {w: len(w) for w in ["hello", "world", "python"]}
# {'hello': 5, 'world': 5, 'python': 6}
```

## 2. with 语句（上下文管理器）

**❌ 忘记关文件：**
```python
f = open("data.txt", "r")
data = f.read()
f.close()  # 容易忘，异常时更危险
```

**✅ 自动管理：**
```python
with open("data.txt", "r") as f:
    data = f.read()
# 出了 with 块，文件自动关闭
```

自定义上下文管理器：
```python
from contextlib import contextmanager

@contextmanager
def timer(label):
    import time
    start = time.time()
    yield
    print(f"{label}: {time.time() - start:.2f}s")

with timer("数据处理"):
    # 你的代码
    pass
```

## 3. 海象运算符 `:=`（Python 3.8+）

避免重复计算同一表达式：

**❌ 重复调用：**
```python
data = get_large_data()
if len(data) > 100:
    print(f"数据量: {len(data)}")
```

**✅ 只算一次：**
```python
if (n := len(get_large_data())) > 100:
    print(f"数据量: {n}")
```

正则匹配场景特别好用：
```python
import re
if (m := re.search(r'\d+', text)):
    print(f"找到数字: {m.group()}")
```

## 4. 解包赋值

```python
# 交换变量
a, b = b, a

# 忽略不需要的值
first, *rest = [1, 2, 3, 4, 5]
# first=1, rest=[2,3,4,5]

# 函数返回多值
def get_user():
    return "张三", 25, "dev"

name, age, role = get_user()
```

## 5. f-string 的隐藏能力

```python
name = "Python"
print(f"{name:=^30}")  # =========Python==========

# 调试神器（Python 3.8+）
x = 42
print(f"{x = }")        # x = 42
print(f"{x + 1 = }")    # x + 1 = 43

# 格式化数字
price = 1234567.89
print(f"¥{price:,.2f}")  # ¥1,234,567.89
```

## 总结

| 技巧 | 替代 | 省代码量 |
|------|------|---------|
| 列表推导 | for + append | 60% |
| with 语句 | try/finally | 40% |
| 海象运算符 | 重复表达式 | 30% |
| 解包赋值 | 逐个赋值 | 50% |
| f-string | format() | 30% |

> 好代码不是写得少，是**用最少的字表达最清晰的意思**。Python 的语法糖不是为了炫技，而是为了让意图更明确。

---

*更多 Python 技巧关注 [击穿二极管](https://diodeshing.github.io/my-blog/)，欢迎 Star [GitHub](https://github.com/diodeshing)。*
