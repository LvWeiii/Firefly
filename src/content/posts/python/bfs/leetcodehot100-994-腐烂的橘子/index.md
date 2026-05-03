---
title: "leetcodehot100-994.腐烂的橘子"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/bfs/leetcodehot100-994-腐烂的橘子"
date: 2026-04-09
---

[[994. 腐烂的橘子 - 力扣（LeetCode）](https://leetcode.cn/problems/rotting-oranges/?envType=study-plan-v2&envId=top-100-liked)]()

```python
from collections import deque
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n = len(grid[0])
        fresh_count = 0
        queue = deque()
        for i in range(m):#记录初始状态
            for j in range(n):
                if grid[i][j] == 1:
                    fresh_count += 1
                elif grid[i][j] == 2:
                    queue.append((i,j))#模板中start对应此处初始的腐烂橘子
        if fresh_count == 0:
            return 0
        minutes = 0
        dx = [-1,1,0,0]
        dy = [0,0,-1,1]
        while fresh_count and queue:
            minutes += 1
            for _ in range(len(queue)):
                x,y = queue.popleft()
                for k in range(4):
                    if 0 <= x+dx[k] < m and 0 <= y+dy[k] < n and grid[x+dx[k]][y+dy[k]] == 1:
                        queue.append((x+dx[k],y+dy[k]))
                        fresh_count -= 1
                        grid[x+dx[k]][y+dy[k]] = 2#等价于模板中visited操作
        return minutes if fresh_count == 0 else -1
```
