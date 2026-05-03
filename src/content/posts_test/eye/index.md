---
title: "eye()"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: true
slug: eye
date: 2026-04-29
---

torch.eye()生成单位矩阵

```python
torch.eye(n, m=None, *, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False)
```

n:行数，必须提供
m:列数，默认为None
dtype:为torch.bool的时候生成对角线为True、其余为False的单位阵
device:张量所在的设备
requires_grad:是否需要梯度，默认为False
