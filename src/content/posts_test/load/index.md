---
title: "map_location参数"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: true
slug: load
date: 2026-04-29
---

`torch.load(f, map_location=None, ...)` 是 PyTorch 用来从磁盘加载之前 `torch.save` 保存的对象的函数。  它可以加载模型权重、优化器状态、普通张量、以及任意 Python 字典等。

# map_location参数

map_location控制加载后的张量存储在哪个设备上，map_location=None的时候自动把张量读取到存储的设备上。
