---
title: defaultdict
published: 2026-05-03
description: ""
tags:
  - collections
  - 数据结构
category: python
draft: false
slug: "python/哈希/defaultdict"
---

# 基本语法 

```python
from collections import defaultdict
d = defaultdict()
```

`defaultdict` 是 Python 中 `collections` 模块提供的一个字典类，它与普通字典的区别在于：当访问一个不存在的键时，`defaultdict` 会自动为该键创建一个默认值，而不是抛出 `KeyError` 异常。
同时也支持普通字典的所有操作

# 常见的默认值工厂函数

int:默认为0
list:默认为空列表[]
set:默认是空集合
str:默认是空字符串“”

# 插入元素
```python
from collections import defaultdict

def main():
    positions = defaultdict(list)
    
    # 示例数据
    a = [1, 2, 3, 2, 1, 2, 3, 2]
    
    # 遍历数组，记录每个数字出现的位置（从1开始计数）
    for i in range(len(a)):
        positions[a[i]].append(i + 1)
    
    # 输出 positions
    for key, value in positions.items():
        print(f"数字 {key} 出现的位置: {' '.join(map(str, value))}")

if __name__ == "__main__":
    main()

```
注意访问字典的键用中括号[]
# 访问下标
```python
positions[x][k - 1]
```

# 创建任意默认值
```python
d = defaultdict(lambda: 'N/A')  # 默认值为字符串 'N/A'
print(d['unknown_key'])  # 输出：N/A
```
使用lambda函数

# 常见用法1：分组

```python
dd = defaultdict(list) 
for word in words: 
	key = len(word) # 按长度分组 
	dd[key].append(word)
```


# 常见用法2：计数

```python
dd = defaultdict(int) 
for item in items: 
	dd[item] += 1
```

计数使用counter更方便：[Counter](/posts/python/哈希/counter/)
