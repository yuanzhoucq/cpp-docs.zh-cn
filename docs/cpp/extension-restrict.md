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
ms.openlocfilehash: 6318e6d78f6c4c4bb6827a79d26bca028dfe3f3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233738"
---
# <a name="__restrict"></a>__restrict

与 **__declspec （ [restrict](../cpp/restrict.md) ）** 修饰符一样， **`__restrict`** 关键字指示符号在当前范围中未使用别名。 **`__restrict`** 关键字 `__declspec ( restrict )` 在下列方面与修饰符不同：

- **`__restrict`** 关键字仅对变量有效，且 `__declspec ( restrict )` 仅对函数声明和定义有效。

- **`__restrict`** 与 **`restrict`** C99 规范类似，但 **`__restrict`** 可在 c + + 或 c 程序中使用。

- **`__restrict`** 使用时，编译器不会传播变量的非别名属性。 也就是说，如果为 **`__restrict`** 非变量分配变量 **`__restrict`** ，则编译器仍会允许非 __restrict 变量使用别名。 这不同于 **`restrict`** C99 规范中关键字的行为。

通常，如果你影响整个函数的行为，则使用 `__declspec ( restrict )` 要好过使用关键字。

为了与早期版本兼容， **_restrict** **`__restrict`** 除非指定了编译器选项[/za " \( 禁用语言扩展](../build/reference/za-ze-disable-language-extensions.md)"，否则 _restrict 是同义词。

在 Visual Studio 2015 及更高版本中， **`__restrict`** 可在 c + + 引用中使用。

> [!NOTE]
> 当用于也具有[volatile](../cpp/volatile-cpp.md)关键字的变量时， **`volatile`** 将优先使用。

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
