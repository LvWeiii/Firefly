---
title: "leetcodehot100-42.接雨水"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-42-接雨水"
date: 2026-04-24
---

[42. 接雨水 - 力扣（LeetCode）](https://leetcode.cn/problems/trapping-rain-water/?envType=study-plan-v2&envId=top-100-liked)

相向双指针，哪个指针小就迭代哪个指针

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        left = 0
        right = len(height) - 1
        left_max = 0
        right_max = 0
        ans = 0
        while left < right:
            left_max = max(left_max,height[left])
            right_max = max(right_max,height[right])
            if left_max < right_max:
                ans += left_max-height[left]
                left += 1
            else:
                ans += right_max - height[right]
                right -= 1
        return ans
```
