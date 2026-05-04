---
title: "leetcodehot100-139.单词拆分"
published: 2026-05-03
description: ""
tags:
  - 力扣
category: python
draft: false
slug: "python/动态规划/leetcodehot100-139-单词拆分"
date: 2026-05-01
---

[139. 单词拆分 - 力扣（LeetCode）](https://leetcode.cn/problems/word-break/?envType=study-plan-v2&envId=top-100-liked)

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        #dp[i]表示s[:i]是否可以被切分,dp[0]为true，其余值为false
        #dp[j]由dp[i]（0到j-1）true+dp[i+1:j]在wordDict中时为true
        m = len(s)
        dp = [False] * (m+1)
        dp[0] = True
        for i in range(1,m+1):
            for j in range(i):
                if dp[j] and s[j:i] in wordDict:
                    dp[i] = True
                    break
        return dp[m]
```

时间复杂度:O($n^2$)
