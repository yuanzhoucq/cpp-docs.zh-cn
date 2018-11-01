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
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454543"
---
# <a name="restrict"></a>__restrict

像 **__declspec ([限制](../cpp/restrict.md))** 修饰符 **__restrict**关键字指示某个符号未在当前作用域中的指定。 **__Restrict**关键字不同于`__declspec ( restrict )`修饰符在以下方面：

- **__Restrict**关键字是仅在变量上有效和`__declspec ( restrict )`仅适用于函数声明和定义。

- **__restrict**类似于**限制**于 C99 规范中，但 **__restrict**可以在 c + + 或 C 程序中使用。

- 当 **__restrict**是使用，编译器将不会传播变量的非别名属性。 也就是说，如果将分配 **__restrict**变量为非 **__restrict**变量时，编译器仍允许非 __restrict 变量使用别名。 这是不同的行为**限制**C99 规范中的关键字。

通常，如果你影响整个函数的行为，则使用 `__declspec ( restrict )` 要好过使用关键字。

与以前版本的兼容性 **_restrict**是的同义词 **__restrict**除非编译器选项[/Za\(禁用语言扩展)](../build/reference/za-ze-disable-language-extensions.md)是指定。

在 Visual Studio 2015 及更高版本， **__restrict**可应用于 c + + 引用。

> [!NOTE]
>  此外具有变量上使用时[可变](../cpp/volatile-cpp.md)关键字**易失性**将优先。

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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)