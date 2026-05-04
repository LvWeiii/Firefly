---
title: "leetcodehot100-283.移动零"
published: 2026-05-03
description: ""
tags:
  - 力扣
category: python
draft: false
slug: "python/双指针/leetcodehot100-283-移动零"
date: 2026-04-22
---

[[283. 移动零 - 力扣（LeetCode）](https://leetcode.cn/problems/move-zeroes/?envType=study-plan-v2&envId=top-100-liked)]()

快慢指针

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        left = 0 #指向已处理数组后一个元素（通常是非零数组后面第一个0）
        for right in range(len(nums)):
            if nums[right] != 0: #left指向0时，是第一个0和当前处理元素交换；left不指向0时，说明此时还没处理过0、left=right，进行一次自交换对结果没影响
                nums[left],nums[right]=nums[right],nums[left]
                left += 1
```
快指针负责遍历处理每个数，而慢指针负责维护已经处理好的区间。每当快指针向右移动的时候，遇到非零数，则将它和慢指针所在位置进行交换，慢指针往后移动，它的移动代表增加已处理区间的长度。

时间复杂度:O(n)

这种一个指针枚举，一个指针维护已处理区间的思想的经典应用场景是快速排序里的"partition"操作。[手撕快速排序](/posts/python/双指针/手撕快速排序/)
