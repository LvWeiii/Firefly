---
title: "创建"
published: 2026-05-03
description: ""
tags:
  - 语法
draft: false
slug: "python/集合/基本语法"
date: 2026-04-07
---

# 创建

s = {1，2，3}

s = set([1,2,2]) 会自动去重变成{1,2}

注意:{}创建的是字典，空集合必须用set() [创建方式](/posts/python/哈希/字典/)

# 添加

s.add(x):添加单个元素

s.update([x,y,z]):批量添加(类似列表的extend)

# 删除

s.remove(x):删除x，如果不存在会抛出错误

s.discard(x):删除x，如果不存在则静默跳过

s.pop():随机弹出一个元素

# 数学运算(并、交、差、补)

并集:s1.union(s2) 合并所有元素，去重

交集:s1.intersection(s2) 仅保留共有的元素

差集:s1.difference(s2) 存在于s1但不在s2

对称差:s1.symmetric_difference(s2) 只在其中一个集合存在的元素

# 集合间的关系判定

是否包含:x in s(这一步比列表快很多)

子集判定:s1.issubset(s2) s1是否在s2里面

超集判定:s1.issuperset(s2) s1是否包含s2

无交集判定:s1.isdisjoint(s2) 如果两个集合完全没有重复元素，返回True

# 性质

由于集合的底层是哈希表，所以查找、添加、删除的时间复杂度是O(1)

# 使用场景

1、去重

2、急速查找:当需要频繁查找且数组很大的时候使用

3、找共性/特性
