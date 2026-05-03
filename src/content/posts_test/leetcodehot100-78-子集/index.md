---
title: "leetcodehot100-78.子集"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: true
slug: "leetcodehot100-78-子集"
date: 2026-04-25
---

[78. 子集 - 力扣（LeetCode）](https://leetcode.cn/problems/subsets/submissions/720953175/?envType=study-plan-v2&envId=top-100-liked)

每一个元素可选可不选，所以是$2^n$情况，使用组合型回溯。可选可不选是二叉树

```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []
        cur = []
        def dfs(index):
            if index == len(nums):
                res.append(cur[:])
                return
            cur.append(nums[index])
            dfs(index+1)
            cur.pop()
            dfs(index+1)
        dfs(0)
        return res
```

回溯的时候push和pop成对出现

时间复杂度:O$(n*2^n$),因为总共输出$2^n$个子集，每个子集输出最多经过n次操作

空间复杂度:O(n)

**注意：**递归时所占用的空间复杂度不是O(2n)O(2n)的。因为有回溯的操作，当一个节点（一次递归函数）算完之后，它会`return` 返回上一层，此时**内存会被当场销毁，给下一次递归复用这片空间**。换句话说，回溯的计算过程是串行计算的，每次只调用一个递归函数，而不是同时运行2n2n个递归函数。

递归时总的空间开销是递归树的高度（又称栈深），为O(n)O(n)的。因为递归的瞬间，当前递归函数会暂存于内存中，等后续递归完成，返回之后才销毁。
