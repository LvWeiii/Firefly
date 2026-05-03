---
title: "常用导入"
published: 2026-05-03
description: ""
tags: []
draft: true
slug: "介绍"
---


# 常用导入

```python
import torch.nn.functional as F
```

导入 PyTorch 函数式接口。F.normalize、F.softmax、F.relu、F.mse_loss 都在这里。

它里面是"无参数函数",与nn.Linear这种"带可训练参数的模块不同"
