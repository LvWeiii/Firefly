---
title: "leetcodehot100-73.矩阵置零"
published: 2026-05-03
description: ""
tags:
  - 力扣
category: python
draft: false
slug: "python/哈希/leetcodehot100-73-矩阵置零"
date: 2026-04-21
---

[[73. 矩阵置零 - 力扣（LeetCode）](https://leetcode.cn/problems/set-matrix-zeroes/?envType=study-plan-v2&envId=top-100-liked)]()

与[leetcodehot100-41.缺失的第一个正数](/posts/python/哈希/leetcodehot100-41-缺失的第一个正数/)一样都是原地哈希

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        row_zero = 1
        col_zero = 1
        for i in range(len(matrix)):
            if matrix[i][0] == 0:
                col_zero = 0
                break
        for i in range(len(matrix[0])):
            if matrix[0][i] == 0:
                row_zero = 0
                break
        for i in range(1,len(matrix)):
            for j in range(1,len(matrix[0])):
                if matrix[i][j] == 0:
                    matrix[0][j] = 0
                    matrix[i][0] = 0
        for i in range(1,len(matrix)):
            if matrix[i][0] == 0:
                for j in range(len(matrix[0])):
                    matrix[i][j] = 0
        for i in range(1,len(matrix[0])):
            if matrix[0][i] == 0:
                for j in range(len(matrix)):
                    matrix[j][i] = 0
        if not col_zero:
            for i in range(len(matrix)):
                matrix[i][0] = 0
        if not row_zero:
            for j in range(len(matrix[0])):
                matrix[0][j] = 0
```

这道题的核心思路是**用矩阵本身充当标记数组**：朴素做法是额外开两个数组，分别记录哪些行和哪些列需要清零；但为了满足原地算法要求，我们把第一行当作列标记，把第一列当作行标记。这样在扫描到某个位置是 `0` 时，就能把对应行列的信息记录到第一行和第一列里。由于第一行和第一列本身也可能原本就要被清零，所以再额外用两个变量单独记录它们的状态。最后根据这些标记统一清零即可。时间复杂度是 **`O(mn)`**，空间复杂度是 **`O(1)`**。
