---
title: "最开始使用了暴力循环"
published: 2026-05-03
description: ""
tags:
  - 力扣
  - 方法论
draft: true
slug: "leetcodehot100-两数之和"
date: 2026-04-09
---

给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 **和为目标值** _`target`_  的那 **两个** 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案，并且你不能使用两次相同的元素。

你可以按任意顺序返回答案。

# 最开始使用了暴力循环

```python
class Solution: 
	def twoSum(self, nums: List[int], target: int) -> List[int]: 
		for i in range(len(nums)-1): 
			for j in range(i+1,len(nums)): 
				if nums[i] + nums[j] == target: 
					return [i,j]
```
时间复杂度为O(n²)

# 优化:使用哈希表以及前缀和的思想

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash = dict({nums[0]:0})
        for i in range(1,len(nums)):
            if target - nums[i] in hash:
                return [i,hash[target-nums[i]]]
            hash[nums[i]] = i
```
时间复杂度降到了O(n)

创建字典更推荐使用:
```python
hash = {nums[0]:0}
```
