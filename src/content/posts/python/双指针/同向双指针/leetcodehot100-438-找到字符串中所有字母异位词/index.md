---
title: "leetcodehot100-438.找到字符串中所有字母异位词"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/双指针/同向双指针/leetcodehot100-438-找到字符串中所有字母异位词"
date: 2026-04-24
---

[438. 找到字符串中所有字母异位词 - 力扣（LeetCode）](https://leetcode.cn/problems/find-all-anagrams-in-a-string/?envType=study-plan-v2&envId=top-100-liked)

这题甚至可以单指针，因为滑动窗口的大小固定
依旧哈希频次表

```python
from collections import defaultdict
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        count_2 = defaultdict(int)
        for ch in p:
            count_2[ch] += 1
        count_1 = defaultdict(int)
        valid = 0
        total = len(count_2)
        n = len(p)
        ans = []
        for i in range(len(s)):
            if s[i] in count_2:
                count_1[s[i]] += 1
                if count_1[s[i]] == count_2[s[i]]:
                    valid += 1
                if count_1[s[i]] - 1 == count_2[s[i]]:
                    valid -= 1
            if i >= n :
                if s[i-n] in count_2:
                    count_1[s[i-n]] -= 1
                    if count_1[s[i-n]] == count_2[s[i-n]]:
                        valid += 1
                    if count_1[s[i-n]] + 1== count_2[s[i-n]]:
                        valid -= 1
            if valid == total:
                ans.append(i-n+1)
        return ans
```

时间复杂度:O(n)
