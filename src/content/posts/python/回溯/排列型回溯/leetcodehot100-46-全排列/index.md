---
title: "leetcodehot100-46.全排列"
published: 2026-05-03
description: ""
tags:
  - 力扣
category: python
draft: false
slug: "python/回溯/排列型回溯/leetcodehot100-46-全排列"
date: 2026-04-25
---

[46. 全排列 - 力扣（LeetCode）](https://leetcode.cn/problems/permutations/submissions/721068252/?envType=study-plan-v2&envId=top-100-liked)

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

- **时间复杂度：$O(N \times N!)$**
    
    第一层有 $N$ 个选择，第二层剩 $N-1$ 个，第三层 $N-2$ 个……一直乘下去就是 $N!$ (阶乘)。当找到一个答案时，拷贝数组还需要 $O(N)$ 的时间。
    
- **空间复杂度：$O(N)$**
    
    递归深度是 $N$，`path` 数组长度是 $N$，`used` 数组长度也是 $N$。所以辅助空间极其优秀，只有 $O(N)$。
