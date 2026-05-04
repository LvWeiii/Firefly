---
title: "华为2025.10.15动态注意力掩码调度问题"
published: 2026-05-03
description: ""
tags:
  - 华为真题
category: python
draft: false
slug: "python/贪心/华为2025-10-15动态注意力掩码调度问题"
date: 2026-04-09
---

[[第2题-动态注意力掩码调度问题 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P4227)]()

```python
import sys
import numpy as np
def rmsnorm(arr,n,d):
    for i in range(n):
        arr[i,:] = arr[i,:] / np.linalg.norm(arr[i,:]) * np.sqrt(d)
def main():
    n,d = map(int,sys.stdin.readline().strip().split())
    data = []
    for _ in range(n):
        tmp = list(map(float,sys.stdin.readline().strip().split()))
        data.append(tmp)
    arr = np.array(data,dtype = np.float64)
    tmp = list(map(int,sys.stdin.readline().strip().split()))
    c = np.array(tmp,dtype = np.int64)
    rmsnorm(arr,n,d)
    A = np.dot(arr,arr.T) / np.sqrt(d)#A[i,j] = Aij
    A = A * A
    S = 0
    for j in range(n):
        if j <= c[j]:#此时所有元素都能取1
            S += sum(A[0:j,j])
        else:#只有前c[j]个元素可以取1
            tmp = np.sort(A[0:j,j])[::-1]#注意numpy数组排序的时候降序不能用reverse=True,而要用[::-1]
            S += sum(tmp[0:c[j]])
    print(S*100)
if __name__ == "__main__":
    main()
```
