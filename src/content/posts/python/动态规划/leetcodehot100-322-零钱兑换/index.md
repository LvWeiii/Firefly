---
title: "leetcodehot100-322.零钱兑换"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/动态规划/leetcodehot100-322-零钱兑换"
date: 2026-05-01
---

[322. 零钱兑换 - 力扣（LeetCode）](https://leetcode.cn/problems/coin-change/submissions/722293737/?envType=study-plan-v2&envId=top-100-liked)

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        #dp[i]表示凑成i金额所需的最少的硬币总数，dp[0]=0,其余值为正无穷（因为min）
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0
        for i in range(1,amount+1):
            for coin in coins:
                if i >= coin:
                    dp[i] = min(dp[i],dp[i-coin]+1)
        return dp[amount] if dp[amount] != float('inf') else -1
```
