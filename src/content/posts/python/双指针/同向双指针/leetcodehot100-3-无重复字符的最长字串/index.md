---
title: "leetcodehot100-3.无重复字符的最长字串"
published: 2026-05-03
description: ""
tags:
  - collections
  - 力扣
category: python
draft: false
slug: "python/双指针/同向双指针/leetcodehot100-3-无重复字符的最长字串"
date: 2026-04-16
---

[[3. 无重复字符的最长子串 - 力扣（LeetCode）](https://leetcode.cn/problems/longest-substring-without-repeating-characters/submissions/718770613/?envType=study-plan-v2&envId=top-100-liked)]()

这个题目是滑动窗口的同向快慢指针

```python
from collections import defaultdict
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        max_len = 0
        left = 0
        dict = defaultdict(int)
        for right in range(len(s)):
            if s[right] in dict and dict[s[right]]+1>left:
                left = dict[s[right]] + 1
            dict[s[right]] = right
            max_len = max(max_len,right-left+1)
        return max_len
```

- **时间复杂度**：$O(n)$，其中 $n$ 是字符串长度。只需遍历一次。
    
- **空间复杂度**：$O(m)$，其中 $m$ 是字符集的大小（比如 ASCII 码只有 128 个，或者是扩展字符集）。
