---
title: "model.train()与model.eval()"
published: 2026-05-03
description: ""
tags:
  - 概念
  - 函数
category: python
draft: false
slug: "python/库/pytorch/model-train-与model-eval"
date: 2026-04-27
---

model.train()是训练模式，model.eval()是评估模式

# 区别

1、model.train()时，Dropout会随机丢弃一部分神经元，用来防止过拟合。
model.eval()时，Dropout会关闭，所有神经元都参与计算，输出更稳定。

2、model.train()时，BatchNorm使用当前batch的均值和方差，并更新自己的running mean/running var。
model.eval()时，BatchNorm不再用当前batch统计量，而是使用训练过程中累积下来的running mean/running var。

# 注意
model.eval()不会关闭梯度计算。
