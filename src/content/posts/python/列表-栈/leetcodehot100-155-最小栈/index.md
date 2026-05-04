---
title: "leetcodehot100-155.最小栈"
published: 2026-05-03
description: ""
tags:
  - 力扣
category: python
draft: false
slug: "python/列表-栈/leetcodehot100-155-最小栈"
date: 2026-04-19
---

[[155. 最小栈 - 力扣（LeetCode）](https://leetcode.cn/problems/min-stack/submissions/719474765/?envType=study-plan-v2&envId=top-100-liked)]()

栈的设计题，以空间换时间

```python
class MinStack:
  
    def __init__(self):
        self.stack = []
  
    def push(self, val: int) -> None:
        if not self.stack:
            self.stack.append((val,val))
        else:
            cur_min = self.stack[-1][1]
            self.stack.append((val,val) if val < cur_min else (val,cur_min))
  
    def pop(self) -> None:
        self.stack.pop()
    def top(self) -> int:
        return self.stack[-1][0]
  
    def getMin(self) -> int:
        return self.stack[-1][1]
  

# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```
