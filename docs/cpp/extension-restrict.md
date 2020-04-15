---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360814"
---
# <a name="__restrict"></a>__restrict

与 **__declspec （[限制](../cpp/restrict.md)）** 修饰符一样 **，__restrict**关键字表示符号在当前作用域中未进行别名。 **__restrict**关键字与`__declspec ( restrict )`修饰符在以下方面有所不同：

- **__restrict**关键字仅在变量上有效，`__declspec ( restrict )`并且仅在函数声明和定义上有效。

- **__restrict**类似于 C99 规范**的限制**，但 **__restrict**可用于C++或 C 程序。

- 使用 **__restrict**时，编译器不会传播变量的无别名属性。 也就是说，如果将 **__restrict**变量分配给非 **__restrict**变量，编译器仍将允许对非__restrict变量进行别名化。 这与 C99 规范中**限制**关键字的行为不同。

通常，如果你影响整个函数的行为，则使用 `__declspec ( restrict )` 要好过使用关键字。

为了与早期版本兼容，**除非**指定编译器选项[/Za\(禁用语言扩展，](../build/reference/za-ze-disable-language-extensions.md)否则_restrict是 **__restrict**的同义词。

在 Visual Studio 2015 及更高版本中 **，__restrict**可用于C++引用。

> [!NOTE]
> 当在也有[易失性](../cpp/volatile-cpp.md)关键字的变量上使用时，**挥发性**将优先。

## <a name="example"></a>示例

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>另请参阅

[Keywords](../cpp/keywords-cpp.md)
