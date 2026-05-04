---
title: "浅拷贝"
published: 2026-05-03
description: ""
tags:
  - 函数
category: python
draft: false
slug: "python/列表-栈/浅拷贝"
date: 2026-04-03
---

`path[:]` 是**创建列表的浅拷贝**，将 `path` 的副本添加到 `result` 中，而不是添加 `path` 本身的引用。

# 原因

```python
# 错误做法：直接添加引用
result = []
path = [1, 2]
result.append(path)      # 添加的是 path 的引用
path.append(3)           # 修改 path
print(result)            # [[1, 2, 3]] - result 中的列表也被修改了！

# 正确做法：添加副本
result = []
path = [1, 2]
result.append(path[:])   # 添加 path 的副本
path.append(3)           # 修改 path
print(result)            # [[1, 2]] - result 中的列表不受影响

```

注意了:一维列表可以用浅拷贝，因为一维列表中的每个元素都是不可迭代的
但是二维列表中每个元素是一个数组的引用，可以迭代，浅拷贝的时候依旧会两个一起修改->使用copy.deepcopy()(需要import copy)
