---
title: "二解：并查集"
published: 2026-05-03
description: ""
tags:
  - 力扣
draft: false
slug: "python/bfs/leetcodehot100-200-岛屿数量"
date: 2026-04-16
---

[[200. 岛屿数量 - 力扣（LeetCode）](https://leetcode.cn/problems/number-of-islands/submissions/718615199/?envType=study-plan-v2&envId=top-100-liked)]()

```python
from collections import deque
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:#注意输入的grid元素是str类型
        if not grid:
            return 0
        res = 0
        m = len(grid)
        n = len(grid[0])
        dx = [-1,1,0,0]
        dy = [0,0,-1,1]
        for i in range(m):
            for j in range(n):
                if grid[i][j] == "1":
                    res += 1
                    queue = deque([(i,j)])
                    grid[i][j] = "0"
                    while queue:
                        x,y = queue.popleft()
                        for k in range(4):
                            if 0 <= x+dx[k] < m and 0 <= y+dy[k] < n and grid[x+dx[k]][y+dy[k]] == "1":
                                queue.append((x+dx[k],y+dy[k]))
                                grid[x+dx[k]][y+dy[k]] = "0"
        return res
```


### 1. 为什么最开始初始化用的是 `deque([(i, j)])`？

`deque` 是一个类，它的构造函数要求传入的是一个**可迭代对象（iterable）**，比如列表、元组或字符串。`deque` 在初始化时，会把这个可迭代对象**拆开**，将其中的元素**逐个**放入队列中。

- **如果直接写 `deque((i, j))`：** Python 会把外层的元组当作可迭代对象给拆了。结果是队列里变成了两个独立的数字：队列变成了类似 `[i, j]` 的状态。当你随后调用 `x, y = queue.popleft()` 时，弹出的只是数字 `i`，无法解包给 `x, y`，程序直接报错。
    
- **所以必须写 `deque([(i, j)])`：** 我们在坐标元组 `(i, j)` 外面套了一个列表 `[]`。`deque` 初始化时拆开这个外层列表，发现里面只有一个元素，就是元组 `(i, j)`，于是把这个元组完整地放进队列里。这样队列的初始状态就是正确的。
    

### 2. 为什么后面入队直接用 `queue.append((x+dx[k], y+dy[k]))`？

`append()` 是一个方法，它的作用是把传入的参数**作为一个整体的单一元素**，直接塞到队列的末尾。它**不会**去拆解你传入的东西。

- 因为我们想往队列里放的数据结构就是一个代表坐标的**元组** `(新x, 新y)`。
    
- 所以，直接把这个元组传给 `append` 就可以了，即 `append((x+dx[k], y+dy[k]))`。
    
- **反向思考：** 如果你在这里写了 `queue.append([(x+dx[k], y+dy[k])])`，那么你放进队列的就会是一个**列表**（里面装着元组）。等下次循环 `popleft()` 把它弹出来并尝试执行 `x, y = ...` 解包时，由于弹出来的是个列表，又会引发报错。


#### Q1：你的空间复杂度是多少？

- **回答**：
    
    - **时间复杂度**：$O(M \times N)$，其中 $M, N$ 分别是行数和列数。每个格子最多进入队列一次。
        
    - **空间复杂度**：最坏情况下是 $O(\min(M, N))$。
        
    - **深度解析**：在 BFS 中，队列里最多同时存在的元素量是岛屿的“宽度”。对于一个满是陆地的矩形，最大宽度是 $\min(M, N)$。
        

#### Q2：为什么你在 `append` 的时候就把 "1" 改成 "0"，而不是在 `popleft` 的时候改？

- **回答**：**这是为了防止重复入队。** 如果在弹出时才修改，同一个点可能会被它周围的四个邻居分别发现并重复加入队列。这会导致队列内存爆炸，时间复杂度也会退化。
    

#### Q3：如果不允许修改原数组 `grid` 怎么办？

- **回答**：
    
    1. 使用一个同等大小的二维布尔数组 `visited = [[False for _ in range(n)] for _ in range(m)]` 来记录访问状态。
        
    2. 面试官如果追问“如何优化这个 `visited` 数组的空间？”，可以提到使用**位图（Bitmask）**或者**并查集（Union Find）**。
        

#### Q4：这道题用 DFS 还是 BFS 更好？

- **回答**：
    
    - **DFS**：代码更简洁，但在岛屿面积非常巨大时，可能会触发 Python 的**递归深度限制**（Recursion Depth Limit）。
        
    - **BFS**：虽然代码稍长，但由于是迭代实现，更**稳健**，不会有栈溢出的风险，通常是大厂面试的首选方案。


# 二解：并查集

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid: return 0
        m, n = len(grid), len(grid[0])
        fa = list(range(m * n))
        self.count = sum(grid[i][j] == '1' for i in range(m) for j in range(n)) # 初始陆地数

        def find(x):
            if fa[x] != x:
                fa[x] = find(fa[x])
            return fa[x]

        def union(u, v):
            root_u, root_v = find(u), find(v)
            if root_u != root_v:
                fa[root_v] = root_u
                self.count -= 1 # 每次合并，岛屿数量减1

        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    # 只需要向右和向下看，避免重复合并
                    for ni, nj in [(i + 1, j), (i, j + 1)]:
                        if ni < m and nj < n and grid[ni][nj] == '1':
                            union(i * n + j, ni * n + nj)
        return self.count
```
