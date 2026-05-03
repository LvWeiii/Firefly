---
title: "参数直接变成：已经用了的左括号数(left)，已经用了的右括号数(right)"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/回溯/排列型回溯/leetcodehot100-22-括号生成"
date: 2026-04-25
---

[22. 括号生成 - 力扣（LeetCode）](https://leetcode.cn/problems/generate-parentheses/submissions/721082311/?envType=study-plan-v2&envId=top-100-liked)

```python
from typing import List

class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        ans = []
        path = []
        
        # 参数直接变成：已经用了的左括号数(left)，已经用了的右括号数(right)
        def backtrack(left, right):
            # 1. 成功出口：当路径长度等于 2*n 时，一定是一个合法的括号组合
            if len(path) == 2 * n:
                ans.append(''.join(path))
                return
            
            # 2. 选左括号：只要口袋里还有左括号，就能选！
            if left < n:
                path.append('(')
                # 直接传 left+1，免去了手动 += 1 和 -= 1 的麻烦，代码更优雅
                backtrack(left + 1, right)
                path.pop()
                
            # 3. 选右括号：只有右边数量少于左边时，才能选！(天然剪枝，绝不会出现非法括号)
            if right < left:
                path.append(')')
                backtrack(left, right + 1)
                path.pop()
                
        backtrack(0, 0)
        return ans
```
