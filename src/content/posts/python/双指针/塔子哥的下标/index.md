---
title: "塔子哥的下标"
published: 2026-05-03
description: ""
tags:
  - 模板
  - 塔子哥算法课
draft: false
slug: "python/双指针/塔子哥的下标"
date: 2026-04-12
---

[[【双指针1】塔子哥的下标 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P14094)]()

这是个经典的左右指针问题，可以当成左右指针的模板

```python
import sys
def main():
    n = int(sys.stdin.readline().strip())
    nums = list(map(int,sys.stdin.readline().strip().split()))
    target = int(sys.stdin.readline().strip())
    left = 0
    right = n - 1
    flag = False
    while left < right:#注意在循环开始前得先保证这是个升序数组
        if nums[left] + nums[right] == target:
            flag = True
            print(left+1,right+1)
            break
        elif nums[left] + nums[right] < target:
            left += 1
        else:
            right -= 1
    if not flag:
        print("-1")
if __name__ == "__main__":
    main()
```
