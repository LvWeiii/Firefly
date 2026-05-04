---
title: "字典创建方式"
published: 2026-05-03
description: ""
tags: []
category: python
draft: false
slug: "python/哈希/字典创建方式"
---


### 1、直接创建

```python
person = {'name': 'Alice', 'age': 25, 'city': 'New York'}
```

### 2、使用dict()构造函数

##### ①传入键值对序列

```python
dict1 = dict([('name', 'Bob'), ('age', 30), ('city', 'London')])
# 结果: {'name': 'Bob', 'age': 30, 'city': 'London'}
```

##### ②传入关键字参数

```python
dict2 = dict(name='Charlie', age=35, city='Paris')
# 结果: {'name': 'Charlie', 'age': 35, 'city': 'Paris'}
```

以上两种方法可以混合使用

# 3、字典推导式

类似于列表推导式，用于通过表达式和循环来创建字典，非常灵活

```python
n = 5
counts = {i: 0 for i in range(1, n + 1)}
# 结果: {1: 0, 2: 0, 3: 0, 4: 0, 5: 0}
```
