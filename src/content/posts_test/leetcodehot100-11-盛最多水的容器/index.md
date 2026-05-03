---
title: "1. 记录当前面积"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-11-盛最多水的容器"
date: 2026-04-24
---

[11. 盛最多水的容器 - 力扣（LeetCode）](https://leetcode.cn/problems/container-with-most-water/?envType=study-plan-v2&envId=top-100-liked)

相向双指针，哪个小动哪个

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        i = 0
        j = len(height) - 1
        ans = 0
        while i < j:
            # 1. 记录当前面积
            ans = max(ans, (j - i) * min(height[i], height[j]))
            # 2. 淘汰短板，开启跳过模式
            if height[i] < height[j]:
                # 设立“标杆”：记录刚淘汰的短板高度
                current_h = height[i]
                i += 1
                while i < j and height[i] <= current_h:
                    i += 1
            else:
                current_h = height[j]
                j -= 1
                while i < j and height[j] <= current_h:
                    j -= 1
        return ans
```
