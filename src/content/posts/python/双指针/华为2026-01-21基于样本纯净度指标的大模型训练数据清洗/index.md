---
title: "华为2026.01.21基于样本纯净度指标的大模型训练数据清洗"
published: 2026-05-03
description: ""
tags:
  - 华为真题
category: python
draft: false
slug: "python/双指针/华为2026-01-21基于样本纯净度指标的大模型训练数据清洗"
date: 2026-04-12
---

[[第2题-基于样本纯净度指标的大模型训练数据清洗方法 - 题目详情 - CodeFun2000](https://codefun2000.com/p/P4547)]()

```python
import sys

def longest_unique_substring_len(s: str) -> int:
    # ASCII 字符集，开 256 大小数组记录最近出现位置
    last = [-1] * 256
    l = 0
    ans = 0

    # 遍历右端指针 r
    for r, ch in enumerate(s):
        idx = ord(ch)  # 将字符映射到 0~255
        # 如果该字符上次出现位置在当前窗口内，移动左端去重
        if last[idx] >= l:
            l = last[idx] + 1
        # 更新该字符最近出现位置
        last[idx] = r
        # 更新答案
        cur_len = r - l + 1
        if cur_len > ans:
            ans = cur_len
    return ans

def main():
    s = sys.stdin.readline().strip()
    if not s:
        return
    print(longest_unique_substring_len(s))

if __name__ == "__main__":
    main()

```
