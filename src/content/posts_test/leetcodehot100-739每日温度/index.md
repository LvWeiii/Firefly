---
title: "leetcodehot100.739每日温度"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-739每日温度"
date: 2026-04-18
---

[[739. 每日温度 - 力扣（LeetCode）](https://leetcode.cn/problems/daily-temperatures/submissions/719152012/?envType=study-plan-v2&envId=top-100-liked)]()

这道题需要求每一天后温度更高的一天，符合单调栈的使用场景

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        stack = []
        ans = [0] * len(temperatures)
        for i,t in enumerate(temperatures):
            while stack and t > temperatures[stack[-1]]:
                tmp = stack.pop()
                ans[tmp] = i - tmp
            stack.append(i)
        return ans
```
