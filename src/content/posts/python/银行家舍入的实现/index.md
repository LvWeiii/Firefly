---
title: "quantize 默认使用 ROUND_HALF_EVEN (银行家舍入)"
published: 2026-05-03
description: ""
tags:
  - decimal
draft: false
slug: "python/银行家舍入的实现"
date: 2026-04-16
---

```python
import sys 
from decimal import Decimal, ROUND_HALF_EVEN 
def banker_round(value, precision=6): #precision表示位数
	""" 使用 Decimal 实现严格的银行家舍入 """ 
	fmt = "0." + "0" * precision 
	# quantize 默认使用 ROUND_HALF_EVEN (银行家舍入) 
	return Decimal(str(value)).quantize(Decimal(fmt), rounding=ROUND_HALF_EVEN)
```
