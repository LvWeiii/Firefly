---
title: "伪代码"
published: 2026-05-03
description: ""
tags:
  - 基类
draft: false
slug: "python/库/pytorch/torch-utils/torch-utils-data/dataset"
date: 2026-04-29
---

# 伪代码

```python
class Dataset(object):
    def __getitem__(self, index):
        raise NotImplementedError   # 你必须覆写这个方法

    def __add__(self, other):        # 支持用 + 拼接两个数据集
        return ConcatDataset([self, other])
```

# 子类要求

1、强制要求:实现__getitem__(self,index)，让数据集能够根据索引返回一个样本

2、通俗要求:实现__len__。`DataLoader` 在需要知道总样本数（比如构造 indices、计算 epoch 结束）时会调用 `len(dataset)`，如果数据集没有实现 `__len__`，PyTorch 会尝试通过不断迭代来推断大小，但那样效率很低，所以约定俗成都需要继承并实现 `__len__`。
