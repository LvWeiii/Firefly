---
title: "leetcodehot100-189.轮转数组"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/列表-栈/leetcodehot100-189-轮转数组"
date: 2026-04-20
---

[[189. 轮转数组 - 力扣（LeetCode）](https://leetcode.cn/problems/rotate-array/?envType=study-plan-v2&envId=top-100-liked)]()

这道题实现了空间复杂度O(1)的数组翻转，还要注意对k进行预处理

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        k = k % len(nums)#这一步必不可少，防止越界
        def my_reverse(arr,start,end):
            while start < end:
                arr[end],arr[start] = arr[start],arr[end]
                end -= 1
                start += 1
        my_reverse(nums,0,len(nums)-1)
        my_reverse(nums,0,k-1)
        my_reverse(nums,k,len(nums)-1)
```
时间复杂度O(n)
空间复杂度O(1)
