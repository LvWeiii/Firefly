---
title: "leetcodehot100-56.合并区间"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-56-合并区间"
date: 2026-04-18
---

[[56. 合并区间 - 力扣（LeetCode）](https://leetcode.cn/problems/merge-intervals/description/?envType=study-plan-v2&envId=top-100-liked)]()

这题就排序后整个栈就完事了

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort()
        stack = [intervals[0]]
        for i in range(1,len(intervals)):
            if intervals[i][0] <= stack[-1][1]:
                stack[-1][1] = max(intervals[i][1],stack[-1][1])
            else:
                stack.append(intervals[i])
        return stack
```
时间复杂度O(nlogn)
空间复杂度O(n)
