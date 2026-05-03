---
title: "判断标准"
published: 2026-05-03
description: ""
tags:
  - 数据结构
draft: false
slug: "python/可迭代对象"
aliases:
  - Iterable
date: 2026-04-03
---

可迭代对象（Iterable）是指可以逐个返回其元素的对象，简单说就是"能被循环遍历的对象"。

# 判断标准

能用for循环遍历的对象就是可迭代对象

# 常见的可迭代对象

```python
# 1. 列表
my_list = [1, 2, 3]
for item in my_list:
    print(item)

# 2. 元组
my_tuple = (1, 2, 3)
for item in my_tuple:
    print(item)

# 3. 字符串
my_string = "abc"
for char in my_string:
    print(char)  # 输出: a, b, c

# 4. 字典（默认遍历键）
my_dict = {'a': 1, 'b': 2}
for key in my_dict:
    print(key)  # 输出: a, b

# 5. 集合
my_set = {1, 2, 3}
for item in my_set:
    print(item)

# 6. range 对象
for num in range(5):
    print(num)  # 输出: 0, 1, 2, 3, 4

# 7. 文件对象
with open('file.txt') as f:
    for line in f:
        print(line)

```

# 不可迭代的对象

```python
# 数字
num = 123
# for i in num:  # 报错: 'int' object is not iterable

# 布尔值
flag = True
# for i in flag:  # 报错: 'bool' object is not iterable

```
