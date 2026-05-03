---
title: "leetcodehot100-17.电话号码的字母组合"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-17-电话号码的字母组合"
date: 2026-04-25
---

[17. 电话号码的字母组合 - 力扣（LeetCode）](https://leetcode.cn/problems/letter-combinations-of-a-phone-number/submissions/721074971/?envType=study-plan-v2&envId=top-100-liked)

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        ans = []
        path = []
        dic = {'2':['a','b','c'],'3':['d','e','f'],'4':['g','h','i'],'5':['j','k','l'],'6':['m','n','o'],'7':['p','q','r','s'],'8':['t','u','v'],'9':['w','x','y','z']}
        def backtrack(index):
            if index == len(digits):
                ans.append(''.join(path))
                return
            for i in range(len(dic[digits[index]])):
                path.append(dic[digits[index]][i])
                backtrack(index+1)
                path.pop()
        backtrack(0)
        return ans
```

时间复杂度：$O(N \times 4^N)$

空间复杂度：$O(N)$
