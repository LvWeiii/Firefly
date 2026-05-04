---
title: "np.argsort()"
published: 2026-05-03
description: ""
tags:
  - 函数
category: python
draft: false
slug: "python/库/numpy/np-argsort"
date: 2026-04-10
---

```python
import numpy as np

dist = np.array([0.8, 0.2, 0.5, 0.1])
labels = np.array(['A', 'B', 'B', 'A'])

# 1. 获取距离从小到大的索引顺序
idx = np.argsort(dist) 
# idx 结果为 [3, 1, 2, 0]

# 2. 根据这个顺序去重新排列标签
sorted_labels = labels[idx] 
# 结果为 ['A', 'B', 'B', 'A']
```

| **方法**         | **返回结果**   | **作用**                  |
| -------------- | ---------- | ----------------------- |
| `np.sort()`    | 排好序的**数值** | 纯粹想看有序的数据。              |
| `np.argsort()` | 排好序的**索引** | 需要根据排序结果去联动操作其他数组（如标签）。 |
