---
title: "查找 'cherry' 的索引"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: true
slug: index
date: 2026-04-05
---

在 Python 中，`list.index(x)` 的作用是**在列表中查找某个元素 `x` 第一次出现的位置，并返回它的索引（下标）**。

### 核心要点

- **返回值：** 返回的是该元素在列表中的整数索引（从 `0` 开始计数）。
    
- **重复元素：** 如果列表中有多个相同的值，它**只返回第一个**匹配项的索引。
    
- **不存在的情况：** 如果括号里的值不在列表中，程序会抛出一个 `ValueError` 报错。
    

---

### 代码示例

Python

```python
fruits = ['apple', 'banana', 'cherry', 'banana']

# 查找 'cherry' 的索引
idx = fruits.index('cherry')
print(idx)  # 输出: 2

# 查找有重复的 'banana'
idx_banana = fruits.index('banana')
print(idx_banana)  # 输出: 1 (只返回第一个找到的索引)
```

---

### 进阶用法

`.index()` 实际上还可以接受另外两个可选参数，用来指定查找的范围：

`list.index(value, start, end)`

- **`start`**: 从哪个索引开始找（包含）。
    
- **`end`**: 查找到哪个索引为止（不包含）。
    

**例子：**

Python

```python
numbers = [10, 20, 30, 40, 20, 50]

# 从索引 2 开始找 20
print(numbers.index(20, 2))  # 输出: 4
```

### 小贴士 💡

为了避免程序因为找不到值而崩溃，通常建议先用 `in` 关键字检查一下，或者使用 `try...except` 捕获异常：

Python

```python
my_list = [1, 2, 3]
val = 5

if val in my_list:
    print(my_list.index(val))
else:
    print(f"列表中没有 {val}")
```
