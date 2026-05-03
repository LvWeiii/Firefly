---
title: "将 tools 文件夹的路径加入搜索名单"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: false
slug: "python/输入输出-acm/sys/sys-path-append"
date: 2026-04-10
---

简单来说，`sys.path.append()` 是 Python 中用来**动态修改模块搜索路径**的方法。如果你发现自己写的文件明明就在文件夹里，但 Python 报错说 `ModuleNotFoundError`（找不到模块），通常就是因为它派上用场的时候。

---

## 1. 核心原理

当你运行 `import` 语句时，Python 会按照一个特定的顺序去寻找对应的文件。这个顺序存储在一个名为 `sys.path` 的**列表**中。

`sys.path` 的组成通常包括：

1. 当前脚本所在的目录。
    
2. 环境变量 `PYTHONPATH` 中设置的目录。
    
3. Python 安装时的标准库目录。
    
4. 第三方库目录（site-packages）。
    

**`sys.path.append(path)` 的作用就是在这个列表的末尾添加一个新的路径。**

---

## 2. 为什么需要它？

假设你的项目结构如下：

Plaintext

```
my_project/
├── main.py
└── tools/
    └── utils.py
```

如果你在 `main.py` 中想直接 `import utils`，但 `tools` 文件夹并不是一个标准的包，或者你在运行位于项目外部的脚本，Python 可能会找不到这个文件。

通过以下代码，你可以强制 Python 去看一眼那个文件夹：

Python

```
import sys

# 将 tools 文件夹的路径加入搜索名单
sys.path.append('/path/to/my_project/tools')

import utils  # 现在可以成功导入了
```

---

## 3. 关键特性与注意事项

### 🔍 临时性

这是最重要的一点：**这种修改是临时的**。

它只在当前运行的程序进程中有效。一旦程序结束，`sys.path` 就会恢复原样。它不会修改你的系统环境变量。

### 📍 顺序问题（Append vs Insert）

- **`append()`**: 把路径加到列表**末尾**。这意味着 Python 会先找标准库和已有的路径，最后才找你加的这个。
    
- **`insert(0, path)`**: 如果你想让你自定义的模块**覆盖**掉同名的系统模块，可以使用 `sys.path.insert(0, '/your/path')`。这样 Python 会优先搜索你指定的路径。
    

### 🛠️ 建议配合 `os` 使用

为了保证代码在不同电脑上都能跑通，建议使用绝对路径：

Python

```
import sys
import os

# 获取当前脚本的绝对路径，并定位到其上级目录
current_dir = os.path.dirname(os.path.abspath(__file__))
target_path = os.path.join(current_dir, 'my_modules')

sys.path.append(target_path)
```

---

## 总结

- **是什么**：向 Python 的模块搜索名单里加一个新地址。
    
- **干什么**：解决“找不到自定义模块”的问题。
    
- **副作用**：只对当前运行的程序有效，不永久改系统设置。
    

**注意：** 在大型工程中，过度依赖 `sys.path.append()` 可能会让路径管理变得混乱。更好的做法通常是使用 `pip install -e .`（开发模式安装）或者正确配置 `PYTHONPATH`。
