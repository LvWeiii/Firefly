---
title: "leetcodehot100-76.最小覆盖子串"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/双指针/同向双指针/leetcodehot100-76-最小覆盖子串"
date: 2026-04-24
---

[76. 最小覆盖子串 - 力扣（LeetCode）](https://leetcode.cn/problems/minimum-window-substring/submissions/720761082/?envType=study-plan-v2&envId=top-100-liked)

同向双指针

```python
from collections import defaultdict
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        count_2 = defaultdict(int) #t的频次表
        for ch in t:
                count_2[ch] += 1
        total = len(count_2) #频次表的字母数量
        valid = 0 #频次表满足的字母数量
        count_1 = defaultdict(int)
        left = 0
        start = -1
        min_len = len(s)+1
        for right in range(len(s)):
            if s[right] in count_2:
                count_1[s[right]] += 1
                if count_1[s[right]] == count_2[s[right]]:
                    valid += 1
            while valid == total:
                if min_len > right - left + 1:
                    min_len = right -left + 1
                    start = left
                if s[left] in count_2:
                    if count_1[s[left]] == count_2[s[left]]:
                        valid -= 1
                    count_1[s[left]] -= 1
                left += 1
        if start == -1:
            return ""
        else:
            return s[start:start+min_len]
```

时间复杂度:O(n)
