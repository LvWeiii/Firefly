---
title: "leetcodehot100-560.和为k的子数组"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-560-和为k的子数组"
date: 2026-04-20
---

[[560. 和为 K 的子数组 - 力扣（LeetCode）](https://leetcode.cn/problems/subarray-sum-equals-k/?envType=study-plan-v2&envId=top-100-liked)]()

这一道题需要使用前缀和以及哈希表

```python
from collections import defaultdict
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        if not nums:
            return 0
        tmp = defaultdict(int)
        tmp[0] = 1
        count = 0
        cur_sum = 0
        for i in range(len(nums)):
            cur_sum += nums[i]
            if cur_sum - k in tmp:
                count += tmp[cur_sum-k]
            tmp[cur_sum] += 1
        return count
```
