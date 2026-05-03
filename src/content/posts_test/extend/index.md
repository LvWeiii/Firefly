---
title: "核心特点"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: true
slug: extend
date: 2026-04-03
---

`.extend()` 是 Python [切片](/posts/列表/)的一个方法，用于将一个[判断标准](/posts/可迭代对象/)中的所有元素添加到列表末尾。

# 核心特点

1. **修改原列表** - 直接在原列表上操作，不返回新列表
2. **接受可迭代对象** - 参数可以是列表、元组、字符串、集合等任何可迭代对象
3. **逐个添加元素** - 将可迭代对象中的每个元素分别添加到列表中

# 示例

```python
# 基本用法
my_list = [1, 2, 3]
my_list.extend([4, 5, 6])
print(my_list)  # [1, 2, 3, 4, 5, 6]

# 用元组扩展
my_list.extend((7, 8))
print(my_list)  # [1, 2, 3, 4, 5, 6, 7, 8]

# 用字符串扩展（字符串是可迭代的）
my_list = ['a', 'b']
my_list.extend('cd')
print(my_list)  # ['a', 'b', 'c', 'd']

# 用集合扩展
my_list = [1, 2]
my_list.extend({3, 4})
print(my_list)  # [1, 2, 3, 4] 或 [1, 2, 4, 3]（集合无序）

```

# 与.append()区别

```python
# append() 添加整个对象作为单个元素
my_list = [1, 2, 3]
my_list.append([4, 5])
print(my_list)  # [1, 2, 3, [4, 5]]

# extend() 添加可迭代对象中的每个元素
my_list = [1, 2, 3]
my_list.extend([4, 5])
print(my_list)  # [1, 2, 3, 4, 5]

```
- `extend()` 比循环使用 `append()` 更高效
- 对于大量元素的添加，`extend()` 是首选方法
