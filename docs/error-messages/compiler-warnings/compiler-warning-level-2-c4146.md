---
title: 编译器警告 （等级 2） C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: 8b3090f1bc3a64752ede4dab2b1e1b5cd800057d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349784"
---
# <a name="compiler-warning-level-2-c4146"></a>编译器警告 （等级 2） C4146

一元负运算符应用于无符号类型，结果仍未签名

无符号的类型可以存放仅非负的值，因此一元负运算 （求反） 通常毫无意义，当应用于无符号类型。 操作数和结果为非负值。

实际上，当程序员试图表达最小整数值，即介于-2147483648 发生此问题。 此值不能编写为介于-2147483648，因为表达式处理分两个阶段：

1. 数字 2147483648 进行计算。 因为它是大于 2147483647 的最大整数值，2147483648 的类型不是[int](../../c-language/integer-types.md)，但`unsigned int`。

1. 一元负应用于具有无符号的结果，也恰好是 2147483648 的值。

结果的无符号的类型可能会导致意外的行为。 如果在比较中，使用该结果，则未签名的比较时可能会使用，例如，另一个操作数是`int`。 这解释了为什么下面的示例程序将打印只需编写一行。

预期的第二个行`1 is greater than the most negative int`，因为不会打印`((unsigned int)1) > 2147483648`为 false。

您可以通过从 limits.h，具有类型使用 INT_MIN 避免 C4146**带符号整型**。

## <a name="example"></a>示例

下面的示例生成 C4146:

```
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