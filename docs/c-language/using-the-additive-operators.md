---
title: 使用加法运算符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 050db08d00d79e3cfee0ab7549532d78a51b1ade
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078863"
---
# <a name="using-the-additive-operators"></a>使用加法运算符

以下示例阐释了加法和减法运算符，它使用这些声明：

```
int i = 4, j;
float x[10];
float *px;
```

这些语句是等效的：

```
px = &x[4 + i];
px = &x[4] + i;
```

`i` 的值乘以 **float** 的长度，再加上 `&x[4]`。 结果指针值是 `x[8]` 的地址。

```
j = &x[i] - &x[i-2];
```

在此示例中，用 `x` 的第五个元素的地址（由 `x[i-2]` 给定）减去 `x` 的第三个元素的地址（由 `x[i]` 给定）。 用 **float** 的长度除以该差值；结果为整数值 2。

## <a name="see-also"></a>请参阅

[C 加法运算符](../c-language/c-additive-operators.md)