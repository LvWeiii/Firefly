---
title: "leetcodehot100-49.字母异位词分组"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/哈希/leetcodehot100-49-字母异位词分组"
date: 2026-04-20
---

[[49. 字母异位词分组 - 力扣（LeetCode）](https://leetcode.cn/problems/group-anagrams/?envType=study-plan-v2&envId=top-100-liked)]()

```python
from collections import defaultdict
from typing import List
class Solution:
    def solution(self,n:int,strs:List[str]) -> List[List[str]]:
        tmp = defaultdict(list)
        for st in strs:
            count = [0] * 26
            for s in st:
                count[ord(s) - ord('a')] += 1
            tmp[tuple(count)].append(st)#注意输入哈希表的必须是可迭代对象，所以把列表转换成元组
        return list(tmp.values())
if __name__ == "__main__":
    n = int(input())
    strs = list(map(str,input().split()))
    sol = Solution()
    ans = sol.solution(n,strs)
    for i in range (len(ans)):
        print(' '.join(map(str,ans[i])))
```
