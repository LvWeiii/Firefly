---
title: "np.unique()"
published: 2026-05-03
description: ""
tags:
  - 函数
category: python
draft: false
slug: "python/库/numpy/np-unique"
date: 2026-04-10
---

`np.unique()` 是 NumPy 中非常实用的函数，它就像是一个**“去重+统计”**的组合工具。

其核心功能可以总结为：**找出数组中唯一的值，并按从小到大排序。**

---

### 1. 基础用法：快速去重

最简单的用法就是把数组中重复的元素删掉。

Python

```
import numpy as np

arr = [3, 1, 2, 1, 3, 2, 0]
u = np.unique(arr)

print(u) 
# 输出: [0 1 2 3]  （去重且排好序了）
```

---

### 2. 进阶用法：频次统计（KNN 常用）

在 KNN 中，我们最关心的是“哪个标签出现的次数最多”。通过设置 `return_counts=True`，它能直接告诉你每个元素出现的次数。

Python

```
labels = ['A', 'B', 'B', 'A', 'B']
values, counts = np.unique(labels, return_counts=True)

print(values) # ['A' 'B']
print(counts) # [2 3]
```

---

### 3. 三个核心可选参数

`np.unique` 之所以强大，是因为它可以返回不同的辅助信息：

|**参数**|**作用**|**结果说明**|
|---|---|---|
|`return_index=True`|返回**第一次出现**的下标|告诉你这些唯一值是从哪里“冒”出来的。|
|`return_inverse=True`|返回**重构下标**|可以通过这个下标和唯一值数组，还原出原始数组。|
|`return_counts=True`|返回**出现次数**|也就是每个元素在数组中出现了多少次。|

---

### 4. 实战：在 KNN 中如何用它决定分类？

假设你找到了 5 个邻居的标签 `neighbors_labels = [1, 2, 2, 1, 2]`，你想知道谁是赢家：

Python

```
import numpy as np

neighbors_labels = [1, 2, 2, 1, 2]

# 1. 统计标签和票数
labels, counts = np.unique(neighbors_labels, return_counts=True)

# 2. 找到最大票数的索引
max_idx = np.argmax(counts)

# 3. 最终胜出的标签
winner = labels[max_idx]

print(f"标签 {labels} 分别对应的票数为 {counts}")
print(f"最终分类结果为: {winner}")
```

---

### 5. 总结

- **去重**：默认功能，且会自动**排序**。
    
- **统计**：开启 `return_counts` 后，它能替代 Python 原生的字典统计或 `Counter` 类，且在处理大规模数字数组时速度极快。
    
- **注意**：它返回的是两个数组，接收时记得写成 `vals, cnts = np.unique(...)`。
