---
title: "OPPO2025.09.27可整除子数组"
published: 2026-05-03
description: ""
tags:
  - OPPO真题
  - 塔子哥算法课
draft: false
slug: "python/双指针/oppo2025-09-27可整除子数组"
date: 2026-04-12
---

[[【双指针6】可整除子数组 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P4320)]()

这道题需要找到满足条件的最小长度，所以需要固定左指针，寻找右指针

```python
import sys
def mod(x,k):#x有几个k的因数
    cnt = 0
    while x % k == 0:
        cnt += 1
        x = x // k
    return cnt
def main():
    n,k = map(int,sys.stdin.readline().strip().split())
    arr = list(map(int,sys.stdin.readline().strip().split()))
    mod2 = mod(arr[0],2)
    mod5 = mod(arr[0],5)
    right = 0
    result = 0
    for left in range(n):
        while min(mod2,mod5) < k and right < n-1:
            right += 1
            mod2 += mod(arr[right],2)
            mod5 += mod(arr[right],5)
        if min(mod2,mod5) >= k:
            result += n - right
        mod2 -= mod(arr[left],2)
        mod5 -= mod(arr[left],5)
    print(result)
if __name__ == "__main__":
    main()
```
