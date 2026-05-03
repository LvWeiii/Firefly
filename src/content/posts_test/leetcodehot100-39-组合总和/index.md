---
title: "leetcodehot100-39.组合总和"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-39-组合总和"
date: 2026-04-25
---

[39. 组合总和 - 力扣（LeetCode）](https://leetcode.cn/problems/combination-sum/submissions/720984105/?envType=study-plan-v2&envId=top-100-liked)

完全套用[组合型回溯模板](/posts/基本思想/)中的模板

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        ans = []
        path = []
        candidates.sort()
        def backtrack(start,cur_target):
            if cur_target == 0:
                ans.append(path[:])
                return
            for i in range(start,len(candidates)):
                if cur_target-candidates[i] < 0:
                    break
                path.append(candidates[i])
                backtrack(i,cur_target-candidates[i])
                path.pop()
        backtrack(0,target)
        return ans
```
