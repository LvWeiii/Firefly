---
title: "leetcodehot100-279.完全平方数"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-279-完全平方数"
date: 2026-05-01
---

[279. 完全平方数 - 力扣（LeetCode）](https://leetcode.cn/problems/perfect-squares/?envType=study-plan-v2&envId=top-100-liked)

```python
import math
class Solution:
    def numSquares(self, n: int) -> int:
        #我这里定义dp[i]是和为i的完全平方数的最少数量
        #dp[i] = min(dp[i-j*j],j为介于[1,sqrt(i)]的整数)+1,dp[0]=0,其余值初始化成正无穷（因为迭代是min）
        dp = [float('inf')] * (n+1)
        dp[0] = 0
        for i in range(1,n+1):
            for j in range(1,int(math.sqrt(i))+1):
                dp[i] = min(dp[i-j*j]+1,dp[i])
        return dp[n]
```
