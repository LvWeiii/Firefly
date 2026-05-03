---
title: "最长连续不重复子序列"
published: 2026-05-03
description: ""
tags:
  - 塔子哥算法课
  - 模板
draft: true
slug: "最长连续不重复子序列"
date: 2026-04-12
---

[[【双指针3】最长连续不重复子序列 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P14096)]()

这是滑动窗口的典型题目

```python
import sys
def main():
    n = int(sys.stdin.readline().strip())
    arr = list(map(int,sys.stdin.readline().strip().split()))
    seen = set()
    res = 1
    left = 0
    for right in range(n):
        while arr[right] in seen:
            seen.remove(arr[left])
            left += 1
        seen.add(arr[right])
        res = max(res,right-left+1)
    print(res)
if __name__ == "__main__":
    main()
```

这里用set()可以自动进行去重。
可以使用字典记录最后一次出现的位置，这样left更新步长不为1，更优化
