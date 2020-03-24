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
ms.openlocfilehash: cb340554bc20516175400c4d14a5d0dba934a313
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188956"
---
# <a name="__restrict"></a>__restrict

与 **__declspec （ [restrict](../cpp/restrict.md) ）** 修饰符一样， **__restrict**关键字指示符号在当前范围中未使用别名。 **__Restrict**关键字不同于 `__declspec ( restrict )` 修饰符，如下所示：

- **__Restrict**关键字仅对变量有效，`__declspec ( restrict )` 只对函数声明和定义有效。

- **__restrict**类似于 C99 规范的**限制**，但可以在或 C 程序中C++使用 **__restrict** 。

- 使用 **__restrict**时，编译器不会传播变量的非别名属性。 也就是说，如果将 **__restrict**变量分配给非 **__restrict**变量，则编译器仍将允许非 __restrict 变量使用别名。 这不同于 C99 规范中**restrict**关键字的行为。

通常，如果你影响整个函数的行为，则使用 `__declspec ( restrict )` 要好过使用关键字。

为了与早期版本兼容， **_restrict**是 **__restrict**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

在 Visual Studio 2015 和更高 **__restrict**版本中，可以对C++引用使用 __restrict。

> [!NOTE]
>  在同时具有[volatile](../cpp/volatile-cpp.md)关键字的变量上使用时，将优先使用**volatile** 。

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

[关键字](../cpp/keywords-cpp.md)
