---
title: "华为2026.01.07基于混淆矩阵，推导分类模型的核心评估指标"
published: 2026-05-03
description: ""
tags:
  - 华为真题
draft: true
slug: "华为2026-01-07基于混淆矩阵-推导分类模型的核心评估指标"
date: 2026-04-10
---

在多分类（$N$ 个类别）中，我们不再是一次性看整个矩阵，而是**轮流将每一个类别视为“正类”（Positive）**，而将所有其他类别统一视为“负类”（Negative）。

[[第2题-基于混淆矩阵，推导分类模型的核心评估指标 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P4538)]()

```python
import sys
import numpy as np
def main():
    pred = list(map(int,sys.stdin.readline().strip().split()))
    trueY = list(map(int,sys.stdin.readline().strip().split()))
    weights = list(map(float,sys.stdin.readline().strip().split()))
    N = len(weights)
    matrix = np.zeros((N,N),dtype=np.int64)
    for i in range(len(pred)):
        matrix[pred[i],trueY[i]] += 1
    precision = 0
    recall = 0
    f1score = 0
    for i in range(N):
        TP = matrix[i,i]
        FP = np.sum(matrix[i,:])-TP
        FN = np.sum(matrix[:,i])-TP
        TN = len(pred) - TP - FP - FN
        tmp1 = 0
        tmp2 = 0
        if TP + FP != 0:
            tmp1 = TP / (TP + FP)
            precision +=weights[i] *  tmp1
        if TP + FN != 0:
            tmp2 = TP / (TP+FN)
            recall +=weights[i] *  tmp2
        if tmp1 != 0 and tmp2 != 0:
            f1score += weights[i] * 2 * tmp1 * tmp2 / (tmp1+tmp2)
    print(f"{precision:.2f} {recall:.2f} {f1score:.2f}")
if __name__ == "__main__":
    main()
```


这个题目数据量小，不使用numpy反而更快:

```python
import sys
def main():
    pred = list(map(int,sys.stdin.readline().strip().split()))
    trueY = list(map(int,sys.stdin.readline().strip().split()))
    weights = list(map(float,sys.stdin.readline().strip().split()))
    N = len(weights)
    matrix = [[0] * N for _ in range(N)]
    for i in range(len(pred)):
        matrix[pred[i]][trueY[i]] += 1
    precision = 0
    recall = 0
    f1score = 0
    for i in range(N):
        TP = matrix[i][i]
        FP = sum(matrix[i][k] for k in range(N))-TP
        FN = sum(matrix[k][i] for k in range(N))-TP
        TN = len(pred) - TP - FP - FN
        tmp1 = 0
        tmp2 = 0
        if TP + FP != 0:
            tmp1 = TP / (TP + FP)
            precision +=weights[i] *  tmp1
        if TP + FN != 0:
            tmp2 = TP / (TP+FN)
            recall +=weights[i] *  tmp2
        if tmp1 != 0 and tmp2 != 0:
            f1score += weights[i] * 2 * tmp1 * tmp2 / (tmp1+tmp2)
    print(f"{precision:.2f} {recall:.2f} {f1score:.2f}")
if __name__ == "__main__":
    main()
```
