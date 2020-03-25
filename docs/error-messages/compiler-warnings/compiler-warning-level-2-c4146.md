---
title: 编译器警告（等级2） C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: cf0c6e9e2c33887082f945f3f2200d808ac13cd2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174253"
---
# <a name="compiler-warning-level-2-c4146"></a>编译器警告（等级2） C4146

一元负运算符应用于无符号类型，结果仍为无符号

无符号类型只能包含非负值，因此一元负号（求反）在应用于无符号类型时通常不适合。 操作数和结果均为非负值。

实际上，当程序员尝试表达最小整数值时，就会发生这种情况，即-2147483648。 不能将此值写为-2147483648，因为该表达式分为两个阶段：

1. 将计算编号2147483648。 因为它大于最大整数值2147483647，所以2147483648的类型不是[int](../../c-language/integer-types.md)，而 `unsigned int`。

1. 一元减号适用于值，具有无符号结果，也就是2147483648。

结果的无符号类型可能导致意外的行为。 如果在比较中使用该结果，则可以使用未签名的比较，例如，当另一个操作数为 `int`时。 这说明了下面的示例程序仅打印一行的原因。

由于 `((unsigned int)1) > 2147483648` 为 false，因此不会打印所需的第二行 `1 is greater than the most negative int`。

可以通过使用 INT_MIN （其类型为**带符号 INT**的 C4146）来避免使用。

## <a name="example"></a>示例

下面的示例生成 C4146：

```cpp
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```
