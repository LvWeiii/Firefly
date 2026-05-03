---
title: "求向量叉积"
published: 2026-05-03
description: ""
tags:
  - 方法论
draft: false
slug: "线性代数/求向量叉积"
date: 2026-04-10
---

在华为的 AI 算法岗笔试或面试中，线性代数是基础中的基础。**叉积（Cross Product）**，也称为外积或向量积，主要在线性代数和计算机图形学中出现。

需要注意的是，叉积主要定义在 **三维空间（$3$D）** 中。

---

### 1. 叉积的代数计算（坐标法）

假设有两个三维向量：

$$\mathbf{a} = (a_1, a_2, a_3)$$

$$\mathbf{b} = (b_1, b_2, b_3)$$

它们的叉积 $\mathbf{c} = \mathbf{a} \times \mathbf{b}$ 可以通过**行列式**的形式来记忆：

$$\mathbf{a} \times \mathbf{b} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \end{vmatrix}$$

展开后的结果是一个**向量**：

- **$x$ 分量**: $a_2b_3 - a_3b_2$
    
- **$y$ 分量**: $a_3b_1 - a_1b_3$
    
- **$z$ 分量**: $a_1b_2 - a_2b_1$
    

> **口诀：** 算哪个分量，就划掉哪一列，剩下的元素交叉相乘再相减（注意 $y$ 分量符号要变号，或者按 $31-13$ 的顺序记）。

---

### 2. 叉积的几何意义

1. **方向：** 遵循**右手定则**。伸出右手，四指从 $\mathbf{a}$ 弯向 $\mathbf{b}$，大拇指指向的方向就是 $\mathbf{a} \times \mathbf{b}$ 的方向。
    
2. **垂直性：** 结果向量 $\mathbf{c}$ 同时垂直于 $\mathbf{a}$ 和 $\mathbf{b}$。
    
3. **模长（大小）：**
    
    $$\|\mathbf{a} \times \mathbf{b}\| = \|\mathbf{a}\| \|\mathbf{b}\| \sin(\theta)$$
    
    其中 $\theta$ 是两个向量之间的夹角。这个模长的物理意义是：**以 $\mathbf{a}$ 和 $\mathbf{b}$ 为邻边构成的平行四边形的面积**。
    

---

### 3. 华为 AI 笔试常见考点（注意事项）

在做选择题时，请务必关注以下性质：

- **反交换律：** $\mathbf{a} \times \mathbf{b} = -(\mathbf{b} \times \mathbf{a})$。（这点和点积不同，方向会反过来）
    
- **共线判定：** 如果 $\mathbf{a} \times \mathbf{b} = \mathbf{0}$（零向量），则说明 $\mathbf{a}$ 和 $\mathbf{b}$ **平行**（夹角为 $0$ 或 $180^\circ$）。
    
- **分配律：** $\mathbf{a} \times (\mathbf{b} + \mathbf{c}) = \mathbf{a} \times \mathbf{b} + \mathbf{a} \times \mathbf{c}$。
    
- **点积 vs 叉积：**
    
    - 点积（Dot Product）结果是**标量**，用于求夹角余弦。
        
    - 叉积（Cross Product）结果是**向量**，用于求法向量或面积。
        

---

### Python 实现（原生 vs NumPy）

虽然你提到华为机考可以先不急着学 NumPy，但了解一下对比对理解有帮助：

**原生 Python 实现：**

Python

```
def cross_product(a, b):
    return [
        a[1]*b[2] - a[2]*b[1],
        a[2]*b[0] - a[0]*b[2],
        a[0]*b[1] - a[1]*b[0]
    ]
```

**NumPy 实现：**

Python

```
import numpy as np
c = np.cross(a, b)
```
