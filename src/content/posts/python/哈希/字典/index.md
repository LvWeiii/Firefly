---
title: "字典"
published: 2026-05-03
description: ""
tags:
  - 数据结构
category: python
draft: false
slug: "python/哈希/字典"
---

# 创建方式

```python
# 空字典 
d = {} 
d = dict() 
# 初始化 
d = {'a': 1, 'b': 2} 
d = dict(a=1, b=2) 
d = dict([('a', 1), ('b', 2)]) 
# 字典推导式 
d = {x: x**2 for x in range(5)} # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

·dict最外面嵌套的一定是括号！


# 常用操作

```python
# 增/改 
d[key] = value # 直接赋值 
d.update({'c': 3, 'd': 4}) # 批量更新 

# 查 
value = d[key] # 不存在会KeyError 
value = d.get(key) # 不存在返回None 
value = d.get(key, 0) # 不存在返回默认值0 
key in d # 判断键是否存在 

# 删 
del d[key] # 删除键值对 
value = d.pop(key) # 删除并返回值，不存在会报错
value = d.pop(key, None) # 不存在返回None而非报错 
d.clear() # 清空字典 

# 遍历 
for key in d: # 遍历键 或者 for key in d.keys()(通常不建议使用)
for value in d.values(): # 遍历值 
for key, value in d.items(): # 遍历键值对
```

# 高级用法

```python
# setdefault：键不存在时设置默认值 
d.setdefault('key', []).append(1) # 等价于下面3行 
if 'key' not in d: 
d['key'] = [] 
d['key'].append(1) 

# 合并字典 (Python 3.9+) 
d1 = {'a': 1} 
d2 = {'b': 2} 
d3 = d1 | d2 # {'a': 1, 'b': 2} 

# 字典排序 
sorted_items = sorted(d.items(), key=lambda x: x[1]) # 按值排序
```

# 使用场景
- 需要存储键值对关系
- 快速查找某个键对应的值
- 统计计数（键是元素，值是次数）  推荐用[Counter](/posts/python/哈希/counter/)
- 建立映射关系（如索引映射）
