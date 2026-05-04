---
title: "华为2026.03.18基于KNN的语音数据分类"
published: 2026-05-03
description: ""
tags:
  - 华为真题
  - 模板
category: "AI知识"
draft: false
slug: "ai知识/knn/华为2026-03-18基于knn的语音数据分类"
date: 2026-04-11
---

[[第3题-基于KNN的语音数据分类 - problem_ide - CodeFun2000](https://codefun2000.com/p/P4626/ide)]()

```python
import sys
from collections import Counter
def distances(node1,node2):
    return sum((a-b)**2 for a,b in zip(node1,node2))
def main():
    line = sys.stdin.read().split()
    N,K = int(line[0]),int(line[1])
    samples = []
    for i in range(N):
        feature = [float(x) for x in line[2+4*i:5+4*i]]
        label = int(line[5+4*i])
        samples.append({'dist':feature,'label':label})
    node = [float(x) for x in line[4*N+2:4*N+5]]
    for neighbor in samples:
        neighbor['dist'] = distances(node,neighbor['dist'])
    samples.sort(key = lambda x:x['dist'])
    res = samples[:K]
    counts = Counter(n['label'] for n in res)
    max_vote = max(counts.values())
    candidate = [x for x,y in counts.items() if y == max_vote]
    ans = 0
    if len(candidate) == 1:
        ans = candidate[0]
    else:
        for n in res:
            if n['label'] in candidate:
                ans = n['label']
                break
    print(ans)
if __name__ =="__main__":
    main()
```
