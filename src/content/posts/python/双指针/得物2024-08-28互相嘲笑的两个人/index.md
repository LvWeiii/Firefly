---
title: "得物2024.08.28互相嘲笑的两个人"
published: 2026-05-03
description: ""
tags:
  - 塔子哥算法课
  - 得物真题
draft: false
slug: "python/双指针/得物2024-08-28互相嘲笑的两个人"
date: 2026-04-12
---

[[【双指针4】互相嘲笑的两个人 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P4327)]()

连续特定元素的滑动窗口

```python
import sys
def main():
    line = list(map(int,sys.stdin.read().split()))
    if not line:
        return
    n = line[0]
    arr = []
    for i in range(n-1):
        arr.append(line[i+2]-line[i+1]-line[i+2+n]+line[i+1+n])
    res = 1
    len = 1
    for i in range(n-1):
        if arr[i] == 0:
            len += 1
            res = max(res,len)
        else:
            len = 1
    print(res)
if __name__ == "__main__":
    main()
```
