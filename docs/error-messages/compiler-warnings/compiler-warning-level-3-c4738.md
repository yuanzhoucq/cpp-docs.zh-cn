---
title: 编译器警告（等级 3）C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: 833546d20454e6104a2d5fcb272bf5bb9518ea44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401574"
---
# <a name="compiler-warning-level-3-c4738"></a>编译器警告（等级 3）C4738

将 32 位浮点型结果存储在内存中，可能会降低性能

C4738 警告或强制转换时，分配的结果传递自变量，或其他操作可能需要进行舍入操作用尽了注册，需使用的内存 （溢出）。 这可能导致性能损失。

若要解决此警告，并避免舍入，使用编译[/fp: fast](../../build/reference/fp-specify-floating-point-behavior.md)或使用`double`而不是`float`。

若要解决此警告，并避免寄存器不足，更改计算顺序和修改你的使用内联

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>示例

下面的示例生成 C4738:

```
// C4738.cpp
// compile with: /c /fp:precise /O2 /W3
// processor: x86
#include <stdio.h>

#pragma warning(default : 4738)

float func(float f)
{
    return f;
}

int main()
{
    extern float f, f1, f2;
    double d = 0.0;

    f1 = func(d);
    f2 = (float) d;
    f = f1 + f2;   // C4738
    printf_s("%f\n", f);
}
```