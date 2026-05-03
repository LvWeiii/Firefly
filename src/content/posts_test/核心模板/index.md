---
title: "核心模板"
published: 2026-05-03
description: ""
tags:
  - 方法论
draft: true
slug: "核心模板"
date: 2026-04-04
---

# 核心模板

入队即标记，按层加步数，队空返-1

```python
from collections import deque 
def bfs(start, target, graph): 
	queue = deque([start])
	visited = set([start]) 
	step = 0 
	while queue: 
		size = len(queue) 
		for _ in range(size): # 按层遍历（求最短路时常用） 
			node = queue.popleft() 
			if node == target: 
				return step 
			for neighbor in graph[node]:
				if neighbor not in visited: 
				visited.add(neighbor) 
				queue.append(neighbor) 
		step += 1 
	return -1 # 未找到
```

# tip1:为什么不用普通列表，而是用deque()？

普通列表pop[0]操作的时间复杂度是o(n)
而deque()的popleft()的时间复杂度是o(1)，降低了时间复杂度

# tip2:起点要提前入队

```python
queue = deque([start]) 
```
等价于
```python
queue = deque()
queue.append(start)
```
起点要提前入队，不能等到循环里再处理，否则第一个节点没有被访问到

# tip3:入队时就要标记，不能等到出队再标记

否则同一个节点可能被多次加入队列

# tip4:循环终止条件

queue为空，意味着所有可达节点都已经处理完毕

# tip5:step += 1的位置

`step += 1` 必须在 `for _ in range(size)` **外面**，代表走完一整层才算一步。

# 优化1：使用set而不是列表

**节点是坐标/字符串等复杂类型时尤其重要**，set 的查询效率远高于 list。 若节点是连续整数（如图的编号），也可以用 `visited = [False] * (n+1)`，同样是 O(1)。

```python
# ❌ 用列表查询
visited = []
if neighbor not in visited:   # O(n)，每次都要遍历整个列表

# ✅ 用集合查询
visited = set()
if neighbor not in visited:   # O(1)，哈希查找

```
# 优化2：

```python
# ✅ 写法1：出队时判断（标准写法）
node = queue.popleft()
if node == target:
    return step

# ✅ 写法2：入队时判断（更早返回，效率略高）
for neighbor in graph[node]:
    if neighbor == target:
        return step + 1
    if neighbor not in visited:
        visited.add(neighbor)
        queue.append(neighbor)

```
两种写法结果相同，写法2在找到目标时**不需要等到下一轮出队**，可以提前返回，竞赛中略微更优。
