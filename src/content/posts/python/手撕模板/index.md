---
title: "手撕模板"
published: 2026-05-03
description: ""
tags:
  - 模板
category: python
draft: false
slug: "python/手撕模板"
date: 2026-04-20
---

```python
class Solution:
    def solution(self, arr):
        """
        核心逻辑函数
        :param arr: 输入数组
        :return: 计算结果
        """
        return sum(arr)


if __name__ == "__main__":
    sol = Solution()

    print(sol.solution([1, 2, 3]))  # 6
    print(sol.solution([1]))        # 1
    print(sol.solution([]))         # 0


```
