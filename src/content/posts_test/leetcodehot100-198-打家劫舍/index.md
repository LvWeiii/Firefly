---
title: "leetcodehot100-198.打家劫舍"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-198-打家劫舍"
date: 2026-05-01
---

[198. 打家劫舍 - 力扣（LeetCode）](https://leetcode.cn/problems/house-robber/description/?envType=study-plan-v2&envId=top-100-liked)

动态规划,dp[i]表示前i天最多偷的金额，第i天分为偷和不偷，不偷的时候等价于dp[i-1]，偷的时候等价于dp[i-2]+nums[i]，两者取最大。此处还采用了滚动数组优化。

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        last_1_dp,last_2_dp=0,0
        for i in range(len(nums)):
            dp = max(last_2_dp,last_1_dp+nums[i])
            last_1_dp,last_2_dp = last_2_dp,dp
        return dp
```

时间复杂度O(n)
空间复杂度O(1)
