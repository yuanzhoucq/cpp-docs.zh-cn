---
title: 编译器错误 C2131
ms.date: 02/28/2019
f1_keywords:
- C2131
helpviewer_keywords:
- C2131
ms.openlocfilehash: 19bdf73efa82e624382446c94642ceddac00bf2e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426952"
---
# <a name="compiler-error-c2131"></a>编译器错误 C2131

> 表达式计算结果不为常量

一个表达式声明为**const**或**constexpr**在编译时的未计算结果为常量。 编译器必须能够确定在它使用的点表达式的值。

## <a name="example"></a>示例

此示例演示一种方法会导致错误 C2131，以及如何修复此错误。

```cpp
// c2131.cpp
// compile by using: cl /EHsc /W4 /c c2131.cpp

struct test
{
    static const int array_size; // To fix, init array_size here.
    int size_array[array_size];  // C2131
};

const int test::array_size = 42;
```

```Output
c2131.cpp
c2131.cpp(7): error C2131: expression did not evaluate to a constant
c2131.cpp(7): note: failure was caused by non-constant arguments or reference to a non-constant symbol
c2131.cpp(7): note: see usage of 'array_size'
```

## <a name="see-also"></a>请参阅

[const](../../cpp/const-cpp.md)<br/>
[constexpr](../../cpp/constexpr-cpp.md)<br/>
