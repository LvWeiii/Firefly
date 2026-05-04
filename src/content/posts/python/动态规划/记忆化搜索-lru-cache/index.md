---
title: "记忆化搜索-lru_cache"
published: 2026-05-03
description: ""
tags:
  - functools
category: python
draft: false
slug: "python/动态规划/记忆化搜索-lru-cache"
date: 2026-04-05
---

在动态规划里面，如果只是递归的话往往会超时，但是使用递归+记忆化搜索就能极大降低时间复杂度

# 基本语法

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def my_function(param1, param2):
    # 你的计算逻辑
    return result
```

**`maxsize`**: 缓存的大小。

- 在机考中，通常建议设为 `None`，表示不限制缓存大小（只要内存够，全存下来）。
    
- 默认是 128，如果你的递归深度或参数组合超过 128，旧的缓存会被删掉，导致效率下降。
