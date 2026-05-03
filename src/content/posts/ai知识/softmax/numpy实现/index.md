---
title: "定义"
published: 2026-05-03
description: ""
tags:
  - 模板
draft: false
slug: "ai知识/softmax/numpy实现"
date: 2026-04-09
---

# 定义
![softmax](./softmax.jpeg)

# numpy实现

```python
def softmax(a):
	exp_a = np.exp(a)
	sum_exp_a = np.sum(exp_a)
	y = exp_a / sum_exp_a
	return y
```

# 针对溢出问题进行优化

![softmax 1](./softmax-1.jpeg)
![softmax 2](./softmax-2.jpeg)

# 溢出优化版numpy实现

```python
def softmax(a):
	c = np.max(a)
	exp_a = np.exp(a-c)
	sum_exp_a = np.sum(exp_a)
	y = exp_a / exp_a
	return y
```
