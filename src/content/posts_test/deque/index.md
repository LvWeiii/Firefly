---
title: "前置库"
published: 2026-05-03
description: ""
tags:
  - 函数
  - collections
draft: true
slug: deque
date: 2026-04-16
---

# 前置库

```python
from collections import deque
```

# 初始化

deque初始化的时候需要填入可迭代对象
所以deque((1,2))相当于将元素1和2分别填入了队列，要传入坐标(1,2)需要deque([(1,2)])
