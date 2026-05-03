---
title: "leetcodehot100-394.字符串解码"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-394-字符串解码"
date: 2026-04-17
---

[[394. 字符串解码 - 力扣（LeetCode）](https://leetcode.cn/problems/decode-string/?envType=study-plan-v2&envId=top-100-liked)]()

```python
class Solution:
    def decodeString(self, s: str) -> str:
        stack = []
        for i in range(len(s)):
            stack.append(s[i])
            if s[i] == ']':
                stack.pop()
                tmp = []
                while stack[-1] != '[':
                    tmp.append(stack.pop())
                stack.pop()
                tmp = tmp[::-1]
                num = 0
                j = 0
                while stack and'0' <= stack[-1] <= '9':
                    num += 10 ** j * int(stack[-1])
                    j += 1
                    stack.pop()
                stack.extend(tmp * num)
        return ''.join(stack)
```

### 1. 核心思想：栈的“后进先出”

这道题的核心是处理**嵌套结构**（如 `3[a2[c]]`）。

- **左括号 `[` 之前的内容**（数字和字母）必须先存起来。
    
- **遇到右括号 `]` 时**，说明当前这一层的内容已经到头了，必须立即“结算”。
    
- **结算后压回栈**：结算出的结果（如 `cc`）可能还是外层括号的一部分（如 `acc`），所以必须重新入栈等待下一次结算。
    

### 2. 为什么用 `stack.extend(tmp * num)`？

- `tmp * num` 生成的是一个重复后的列表（例如 `['c', 'c']`）。
    
- `extend` 会把列表里的每个元素**平铺**着放进栈里，而不是把整个列表当作一个元素。
    
- **面试官追问**：如果这里用 `stack.append(tmp * num)` 会怎样？
    
    - **答**：会导致栈里出现“嵌套列表”（例如 `['a', ['c', 'c']]`），这样下次 `pop()` 时拿到的就不是单个字符，逻辑会崩溃。
        

### 3. 复杂度分析

- **时间复杂度**：$O(N + L)$，其中 $N$ 是原字符串长度，$L$ 是解码后字符串的总长度。我们需要遍历一遍 $N$，但拼接字符串的过程取决于结果的长度。
    
- **空间复杂度**：$O(L)$。在最坏情况下，栈需要存储解码后的所有字符。
