---
title: 编译器错误 C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 6961d99d1a0d7d0ea063aee5544a1009af2547c7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031256"
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