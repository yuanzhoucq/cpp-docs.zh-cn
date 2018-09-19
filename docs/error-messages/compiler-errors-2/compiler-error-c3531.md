---
title: 编译器错误 C3531 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3531
dev_langs:
- C++
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 375eb419e3f2f492df328a964eeb1bb77bc0d5dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106839"
---
# <a name="compiler-error-c3531"></a>编译器错误 C3531

symbol： 类型包含 auto 的符号必须具有初始值设定项

指定的变量不具有初始值设定项表达式。

### <a name="to-correct-this-error"></a>更正此错误

1. 指定的初始值设定项表达式，如使用等号语法声明变量时的简单分配。

## <a name="example"></a>示例

下面的示例会产生 C3531，因为变量`x1`， `y1, y2, y3`，和`z2`未初始化。

```
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)