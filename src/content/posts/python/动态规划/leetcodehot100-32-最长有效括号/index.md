---
title: "leetcodehot100-32.最长有效括号"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/动态规划/leetcodehot100-32-最长有效括号"
date: 2026-05-01
---

[32. 最长有效括号 - 力扣（LeetCode）](https://leetcode.cn/problems/longest-valid-parentheses/?envType=study-plan-v2&envId=top-100-liked)

```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        #dp[i]表示以i结尾的最长有效括号子串的长度
        #s[i]为'('时肯定不是结尾，此时dp[i]=0
        #s[i]为')'时可以是结尾，dp[i] = dp[i-1]+2(dp[i-1]左边为')'时)，dp[i] = dp[i-1]+2+dp[i-2-dp[i-1]](dp[i-1]左边为'('时)
        m = len(s)
        dp = [0] * (m+1)
        for i in range(1,m):
            tmp = i-1-dp[i-1]
            if s[i] == ')' and tmp>=0 and s[tmp] == '(':
                if  tmp-1 >= 0:
                    dp[i] = dp[i-1] + 2 + dp[tmp-1]
                else:
                    dp[i] = dp[i-1] + 2
        return max(dp)
```

时间复杂度:O(n)
空间复杂度:O(n)
