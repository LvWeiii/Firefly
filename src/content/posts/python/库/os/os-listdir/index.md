---
title: "os.listdir()"
published: 2026-05-03
description: ""
tags:
  - 函数
draft: false
slug: "python/库/os/os-listdir"
date: 2026-04-29
---

os.listdir(IMG_DIR)意思是列出IMG_DIR这个文件夹下面的所有文件名/文件夹名

比如:
IMG_DIR = "/data/img_align_celeba"

如果里面有:
000001.jpg
000002.jpg
000003.jpg

那么返回的是一个列表:
["000001.jpg", "000002.jpg", "000003.jpg"]
注意返回的是名字，而不是完整路径
