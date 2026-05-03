---
title: "1. 单独初始化第一行的数据"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/动态规划/leetcodehot100-64-最小路径和"
date: 2026-04-18
---

[[64. 最小路径和 - 力扣（LeetCode）](https://leetcode.cn/problems/minimum-path-sum/?envType=study-plan-v2&envId=top-100-liked)]()

```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n = len(grid[0])
        dp = [0] * n
        # 1. 单独初始化第一行的数据
        dp[0] = grid[0][0]
        for j in range(1, n):
            dp[j] = dp[j-1] + grid[0][j]
        # 2. 从第二行开始，逐行向下滚动更新
        for i in range(1, m):
            # 每一行的第一列只能从上面走下来，所以直接加上当前格子的值
            dp[0] = dp[0] + grid[i][0]
            for j in range(1, n):
                # 这里的 dp[j] 在被赋值前，里面存的还是上一行的数据 (相当于二维里的 dp[i-1][j])
                # 这里的 dp[j-1] 刚刚在这一轮被更新过，存的是当前行左边的数据 (相当于二维里的 dp[i][j-1])
                dp[j] = min(dp[j], dp[j-1]) + grid[i][j]
        return dp[n-1]
```
时间复杂度：$O(M \times N)$
空间复杂度：$O(N)$
