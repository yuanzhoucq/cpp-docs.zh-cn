---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: e12855127e417472eb88c951b71881240b808013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214199"
---
# <a name="__noop"></a>__noop

**Microsoft 专用**

**`__noop`** 内部函数指定应忽略某个函数。 参数列表已经过分析，但没有为参数生成任何代码。 它旨在用于采用可变数量的参数的全局调试函数。

编译器 **`__noop`** 在编译时将内部转换为0。

## <a name="example"></a>示例

下面的代码演示如何使用 **`__noop`** 。

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[关键字](../cpp/keywords-cpp.md)
