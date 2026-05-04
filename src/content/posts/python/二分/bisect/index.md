---
title: bisect
published: 2026-05-03
description: ""
tags:
  - bisect
category: python
draft: false
slug: "python/二分/bisect"
---

# 库

```python
import bisect
```


# bisect_left函数

`bisect_left` 函数返回目标值**不小于**目标值的位置索引。简言之，它返回数组中第一个不小于指定值的元素的位置。如果指定值已经存在，返回该元素第一次出现的位置。

```python
import bisect
arr = [1, 3, 3, 5, 7]
position = bisect.bisect_left(arr, 3)
print(position)  # 输出 1
```

# bisect_right函数

`bisect_right` 函数返回目标值**大于**目标值的位置索引。如果指定值已经存在，它返回该值**最后一次**出现后的下一个位置。

```python
import bisect
arr = [1, 3, 3, 5, 7]
position = bisect.bisect_right(arr, 3)
print(position)  # 输出 3
```
