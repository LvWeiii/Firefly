---
title: "leetcodehot100-131.分割回文串"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-131-分割回文串"
date: 2026-04-25
---

[131. 分割回文串 - 力扣（LeetCode）](https://leetcode.cn/problems/palindrome-partitioning/?envType=study-plan-v2&envId=top-100-liked)

依旧[组合型回溯模板](/posts/基本思想/)模板套用，这里起点是分割串的起点、range里的起点是分割串的终点，其他都常规

```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        ans = []
        path = []
        def is_huiwen(arr):
            l , r = 0 ,len(arr)-1
            while l < r:
                if arr[l] != arr[r]:
                    return False
                l += 1
                r -= 1
            return True
        def backtrack(start_index):
            if start_index == len(s):
                ans.append(path[:])
                return
            for i in range(start_index,len(s)):
                tmp = s[start_index:i+1]
                if not is_huiwen(tmp):
                    continue
                path.append(tmp)
                backtrack(i+1)
                path.pop()
        backtrack(0)
        return ans
```

- **时间复杂度：$O(N \times 2^N)$**，其中 $N$ 是字符串的长度。
    
- **空间复杂度：$O(N)$**（辅助空间，不包含返回结果所占的空间）。
