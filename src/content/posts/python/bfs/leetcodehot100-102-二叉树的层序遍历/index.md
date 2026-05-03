---
title: "Definition for a binary tree node."
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/bfs/leetcodehot100-102-二叉树的层序遍历"
date: 2026-04-19
---

[[102. 二叉树的层序遍历 - 力扣（LeetCode）](https://leetcode.cn/problems/binary-tree-level-order-traversal/?envType=study-plan-v2&envId=top-100-liked)]()

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
from collections import deque
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if  not root:
            return []
        queue = deque([root])
        res = []
        while queue:
            size = len(queue)
            tmp = []
            for _ in range(size):
                node = queue.popleft()
                tmp.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            res.append(tmp)
        return res
```
