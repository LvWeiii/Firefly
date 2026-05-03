---
title: "两个指针分别指向两个列表的当前区间"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/双指针/同向双指针/leetcodehot100-986-区间列表的交集"
date: 2026-04-24
---

[986. 区间列表的交集 - 力扣（LeetCode）](https://leetcode.cn/problems/interval-list-intersections/submissions/720772128/)

同向双指针，并集的判断和迭代是重点

```python
class Solution:
    def intervalIntersection(self, firstList: List[List[int]], secondList: List[List[int]]) -> List[List[int]]:
        # 两个指针分别指向两个列表的当前区间
        i, j = 0, 0
        ans = []
        # 只要有一个列表遍历完了，就不可能再有交集了
        while i < len(firstList) and j < len(secondList):
            # 获取当前两个区间的起点和终点
            a1, a2 = firstList[i][0], firstList[i][1]
            b1, b2 = secondList[j][0], secondList[j][1]
            # 核心逻辑：计算可能交集的起点和终点
            start = max(a1, b1)
            end = min(a2, b2)
            # 如果起点 <= 终点，说明确实存在交集
            if start <= end:
                ans.append([start, end])
            # 核心逻辑：谁的终点比较小，说明它不可能再和对面的下一个区间有交集了，所以指针前进
            if a2 < b2:
                i += 1
            else:
                j += 1
        return ans
```
