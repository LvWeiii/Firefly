---
title: "leetcodehot100-128.最长连续序列"
published: 2026-05-03
description: ""
tags:
  - 力扣
category: python
draft: false
slug: "python/哈希/leetcodehot100-128-最长连续序列"
date: 2026-04-20
---

[[128. 最长连续序列 - 力扣（LeetCode）](https://leetcode.cn/problems/longest-consecutive-sequence/submissions/719762773/?envType=study-plan-v2&envId=top-100-liked)]()

一个朴素的思路是：用数组构建哈希，枚举所有点xx作为起点，循环地哈希查询x+1,x+2,...x+1,x+2,...来寻找它的最长连续序列，一直到不存在x+k , 此时以x作为起点的长度就是k

这样的复杂度是O(n2)的，因为可能存在如下序列使得每个点都需要往后寻找很多数:

[1,2,3,...,n][1,2,3,...,n]

一个比较巧妙的点在于：**考虑最优解的性质：**

[x1,x2,x3,...,xk][x1​,x2​,x3​,...,xk​]

中的开头元素：x1x1​ 一定满足 : 数组中不存在yy 满足y=x1−1

原因很简单，因为如果有这样的y=x1−1 , 那么显然最优解可以更大。

换句话说，我们上述算法可以优化的点是：没必要枚举所有点作为起点，而是枚举"不存在x−1" 的x作为起点。

因为那些存在x−1的x作为起点，一定不会比现在的答案更优。

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        if not nums:
            return 0
        tmp = set(nums)
        len_max = 0
        for ch in tmp:
            if ch-1 not in tmp:
                tmp_len_max = 1
                tmp_ch = ch
                while tmp_ch+1 in tmp:
                    tmp_len_max += 1
                    tmp_ch += 1
                len_max = max(len_max,tmp_len_max)
        return len_max
```

时间复杂度:O(n)
