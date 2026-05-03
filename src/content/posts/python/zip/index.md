---
title: "输出: [('Alice', 85), ('Bob', 90), ('Charlie', 95)]"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: false
slug: python/zip
date: 2026-04-11
---

### 核心逻辑：像拉链一样配对

如果你有两个列表，一个存名字，一个存分数，`zip()` 会把它们按顺序一一对应。

```python
names = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 95]

zipped = zip(names, scores)
print(list(zipped)) 
# 输出: [('Alice', 85), ('Bob', 90), ('Charlie', 95)]
```

#### 可以解压（Unzip）

如果你有一堆配对好的数据，想把它们拆回两个独立的序列，可以利用 `*` 操作符。


```python
pairs = [('Alice', 85), ('Bob', 90)]
names, scores = zip(*pairs)

print(names)  # ('Alice', 'Bob')
print(scores) # (85, 90)
```

### 字典转换的高级技巧

如果你想把两个列表快速变成字典，`zip()` 是最快的方法：


```python
keys = ['name', 'age', 'city']
values = ['Gemini', 1, 'Cloud']

info = dict(zip(keys, values))
print(info)
# {'name': 'Gemini', 'age': 1, 'city': 'Cloud'}
```

# 应用:计算n维两点距离(省略了开方)

```python
dist = sum((a - b)**2 for a, b in zip(node1, node2))
```
