---
title: 编译器警告（等级 1）C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 492fe4a75b4ddf9b5f78810226f14aa84ab2b56a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176125"
---
# <a name="compiler-warning-level-1-c4163"></a>编译器警告（等级 1）C4163

“identifier”：不可用作内部函数

指定的函数不能用作 [intrinsic](../../preprocessor/intrinsic.md) 函数。 编译器将忽略无效的函数名称。

以下示例生成 C4163：

```cpp
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```
