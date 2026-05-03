---
title: "工作流程"
published: 2026-05-03
description: ""
tags:
  - 经典大模型
draft: false
slug: "ai知识/lstm"
date: 2026-03-29T21:31:00
---

基于[基本形式](/posts/ai知识/rnn/)，缓解梯度消失问题，改善循环神经网络的长程依赖问题

和RNN相比，多了记忆单元$c_{t}$

# 工作流程
![LSTM.1](./lstm-1.png)![LSTM.2](./lstm-2.png)
![LSTM.3](./lstm-3.png)![LSTM.4](./lstm-4.png)
![LSTM.5](./lstm-5.png)
# 为什么LSTM能缓解梯度消失的问题
![LSTM.6](./lstm-6.png)RNN反向传播是连乘，LSTM引入的长期记忆核心路径$c_{t}$反向传播是遗忘门$f_{t}$连乘，控制$f_{t}$稳定在1左右即可
