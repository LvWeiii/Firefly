---
title: "并查集递归模板"
published: 2026-05-03
description: ""
tags:
  - 模板
  - 方法论
category: python
draft: false
slug: "python/并查集/并查集递归模板"
date: 2026-04-06
---

```python
fa = list(range(n+1))#n还是n+1取决于根节点编号是0还是1
def find(x):
	if fa[x] == x:
		return x
	fa[x] = find(fa[x])#路径压缩,找根节点的时候顺便把路径上的点连到根节点上
	return fa[x]
def union(u,v):
	if find(u) != find(v):
		fa[find(v)] = find(u)
```

递归别忘记我们的[递归默认前缀](/posts/python/dfs/递归默认前缀/)
