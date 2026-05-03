---
title: "中国电信2024.10.26序列整除"
published: 2026-05-03
description: ""
tags:
  - 中国电信真题
  - 塔子哥算法课
draft: true
slug: "中国电信2024-10-26序列整除"
date: 2026-04-12
---

[[【双指针5】序列整除 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P4328)]()

这道题属于恰好k个元素x的区间个数，需要转换成最多k个元素x的区间个数减去最多k-1个元素x的区间个数

```python
import sys
def m(arr,k):
    left = 0
    result = 0
    count = 0
    for right in range(len(arr)):
        if arr[right] == 0:
            count += 1
        while count > k:
            if arr[left] == 0:
                count -= 1
            left += 1
        result += right - left + 1
    return result
def main():
    a = list(map(int,sys.stdin.readline().strip().split()))
    x,k = map(int,sys.stdin.readline().strip().split())
    arr = []
    for i in range(len(a)):
        arr.append(a[i]%x)
    print(m(arr,k)-m(arr,k-1) if k != 0 else m(arr,k))
if __name__ == "__main__":
    main()
```
