---
title: "leetcodehot100-152.乘积最大数组"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/动态规划/leetcodehot100-152-乘积最大数组"
date: 2026-05-01
---

[152. 乘积最大子数组 - 力扣（LeetCode）](https://leetcode.cn/problems/maximum-product-subarray/submissions/722310724/?envType=study-plan-v2&envId=top-100-liked)

动态规划以及滚动数组优化

```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        #dp[i][1]表示第i个元素结尾的非空连续子数组的乘积最大值,dp[i][0]是乘积最小值
        #nums[i]大于0时，dp[i][1]=max(dp[i-1][1]*nums[i],nums[i]),dp[i][0]=min(dp[i-1][0]*nums[i],nums[i])
        #nums[i]小于0时，dp[i][1]=max(dp[i-1][0]*nums[i],nums[i]),dp[i][0]=min(dp[i-1][1]*nums[i],nums[i])
        cur_max = cur_min = ans = nums[0]
        for i in range(1,len(nums)):
            if nums[i] > 0:
                now_max = max(cur_max*nums[i],nums[i])
                now_min = min(cur_min*nums[i],nums[i])
            else:
                now_max = max(cur_min*nums[i],nums[i])
                now_min = min(cur_max*nums[i],nums[i])
            cur_max = now_max
            cur_min = now_min
            ans = max(ans,cur_max)
        return ans
```

时间复杂度:O(n)
空间复杂度:O(1)
