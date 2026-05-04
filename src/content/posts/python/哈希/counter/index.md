---
title: Counter
published: 2026-05-03
description: ""
tags:
  - 数据结构
  - collections
category: python
draft: false
slug: "python/哈希/counter"
---

# 本质
dict的子类，专门用于计数

# 基本语法

```python
dd = defaultdict(int) for item in items: dd[item] += 1
```

# 创建方式

```python
# 从列表创建 
c = Counter([1, 2, 2, 3, 3, 3]) # Counter({3: 3, 2: 2, 1: 1}) 

# 从字符串创建 
c = Counter('hello') # Counter({'l': 2, 'h': 1, 'e': 1, 'o': 1}) 

# 从字典创建 
c = Counter({'a': 3, 'b': 2}) 

# 空Counter 
c = Counter()
```

# 访问最常见元素

```python
c = Counter('abracadabra')

c.most_common() # [('a', 5), ('b', 2), ('r', 2), ...] 

c.most_common(2) # [('a', 5), ('b', 2)] 前2个
```

# 展开所有元素

```python
list(c.elements()) # ['a', 'a', 'a', 'a', 'a', 'b', 'b', ...]
```


# 更新计数

```python
c.update('aaa') # 增加计数 
c.subtract('ab') # 减少计数（可以为负）
```

# 删除0和负数计数

```python
c = +c # 只保留正数计数
```

# 运算法则

```python
c1 = Counter('aab') # Counter({'a': 2, 'b': 1}) 
c2 = Counter('abc') # Counter({'a': 1, 'b': 1, 'c': 1}) 
# 加法 
c1 + c2 # Counter({'a': 3, 'b': 2, 'c': 1}) 
# 减法（只保留正数） 
c1 - c2 # Counter({'a': 1}) 
# 交集（取最小值） 
c1 & c2 # Counter({'a': 1, 'b': 1}) 
# 并集（取最大值） 
c1 | c2 # Counter({'a': 2, 'b': 1, 'c': 1})
```

# 应用

### 1、统计字符、元素出现的次数

### 2、Topk问题

```python
def topKFrequent(nums, k): 
	return [x for x, _ in Counter(nums).most_common(k)]
```

### 3、判断两个字符串是否为字母异位词（字母相同、排列方式不同）

```python
def isAnagram(s, t): return Counter(s) == Counter(t)
```
