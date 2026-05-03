---
title: "组合型回溯模板"
published: 2026-05-03
description: ""
tags:
  - 模板
draft: true
slug: "基本思想"
date: 2026-04-16
---

# 组合型回溯模板

```python
def backtrack(起点, 状态): 
	if 满足条件: 记录答案, return 
	for i in range(起点, 结尾): 
		做选择 (append) 
		backtrack(新的起点, 新的状态) 
		撤销选择 (pop)
```

所有情况是$2^n$时，使用组合型回溯；所有情况是n!时，使用排列型回溯

- **组合（不讲究顺序）：** `[1, 2]` 和 `[2, 1]` 是一回事。为了防止重复，我们规定只能**“一直往后走，绝对不回头”**。所以我们发明了 `start_index`，每一层的 `for` 循环都从 `start_index` 开始。
    
- **排列（讲究顺序）：** `[1, 2]` 和 `[2, 1]` 是两个完全不同的合法答案。这意味着，即使我先选了 `2`，我下一轮依然要**“回头”**去选 `1`。
    
    - **这就引出了排列的第一法则：绝对不能用 `start_index`！每一层的 `for` 循环，必须死板地从 `0` 开始扫！**
        

但是，如果每次都从 `0` 开始扫，就会引发一个新的致命问题：你怎么保证不会选出 `[1, 1, 1]` 这种把同一个数字用无数次的答案？

**这就引出了排列的第二法则：引入 `used`（或 `visited`）数组，用来记录“当前这根枝条上，谁已经被用过了”。**

# 排列型回溯模板 以leetcodehot100.46全排列为例

```python
from typing import List

class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        ans = []
        path = []
        
        # 【排列专属零件】：一个和 nums 一样长的布尔数组，记录谁被用过
        used = [False] * len(nums)

        # 【重点】：排列不需要 start_index 这个参数了！
        def backtrack():
            # 1. 成功出口：凑齐了和 nums 一样长的数字，全排列完成
            if len(path) == len(nums):
                ans.append(path[:])
                return
            
            # 2. 横向遍历：永远、永远、永远从 0 开始扫！
            for i in range(len(nums)):
                # 3. 排列的专属剪枝（防重）：
                # 如果这个数字在当前的路径里已经被挑走过了，直接跳过
                if used[i]:
                    continue
                
                # 4. 做选择
                path.append(nums[i])
                used[i] = True  # 标记为已使用
                
                # 5. 递归进入下一层（注意这里啥参数都不用传）
                backtrack()
                
                # 6. 撤销选择：回溯
                used[i] = False # 吐出来之后，标记为未使用，留给别的分支用
                path.pop()

        backtrack()
        return ans
```
