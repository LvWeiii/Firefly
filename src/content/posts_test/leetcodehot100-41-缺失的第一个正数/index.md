---
title: "leetcodehot100-41.缺失的第一个正数"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-41-缺失的第一个正数"
date: 2026-04-20
---

[[41. 缺失的第一个正数 - 力扣（LeetCode）](https://leetcode.cn/problems/first-missing-positive/?envType=study-plan-v2&envId=top-100-liked)]()

原地哈希

```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        n = len(nums)
        for i in range(n):
            while 0 < nums[i] <= n and nums[nums[i]-1] != nums[i]:#注意
                nums[nums[i]-1],nums[i] = nums[i],nums[nums[i]-1]
        for i in range(n):
            if nums[i] != i+1:
                return i+1
        return n+1
```
