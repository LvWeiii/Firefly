---
title: "leetcodehot100-有效的括号"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/列表-栈/leetcodehot100-有效的括号"
date: 2026-04-16
---

[[20. 有效的括号 - 力扣（LeetCode）](https://leetcode.cn/problems/valid-parentheses/description/?envType=study-plan-v2&envId=top-100-liked)]()

后进先出选用栈

```python
class Solution:
    def isValid(self, s: str) -> bool:
        flag = True
        tmp = []
        i = 0
        dic = {')':'(',']':'[','}':'{'}
        for ch in s:
            if ch in dic:
                if not tmp or tmp[-1] != dic[ch]:
                    return False
                else:
                    tmp.pop()
            else:
                tmp.append(ch)
        return not tmp
```


时间复杂度:O(n) 最坏情况相当于遍历一遍数组，里面的pop和append都是O(1)操作

空间复杂度:O(n) 最坏情况相当于遍历一遍数组、全都进栈
