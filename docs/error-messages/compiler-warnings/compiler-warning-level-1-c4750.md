---
title: 编译器警告（等级 1）C4750
description: 介绍 MSVC 编译器警告 C4750 关于可能的堆栈溢出。
ms.date: 07/08/2020
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 9a22bdda407b02b8723b7198d62289d39f62792d
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180963"
---
# <a name="compiler-warning-level-1-c4750"></a>编译器警告（等级 1）C4750

> "*identifier*"：使用 _alloca ( # A1 内联到循环中的函数

## <a name="remarks"></a>备注

"*Identifier*" 函数在 [`_alloca`](../../c-runtime-library/reference/alloca.md) 循环内强制执行函数的内联扩展，这在执行循环时可能导致堆栈溢出。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保 "*identifier*" 函数未通过说明符进行修改 [`__forceinline`](../../cpp/inline-functions-cpp.md) 。

1. 确保 "*identifier*" 函数不包含 [`_alloca`](../../c-runtime-library/reference/alloca.md) 循环中包含的函数。

1. 不要指定 [`/O1`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 、 [`/O2`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 、 [`/Ox`](../../build/reference/ox-full-optimization.md) 或 [`/Og`](../../build/reference/og-global-optimizations.md) 编译开关。

1. 将 [`_alloca`](../../c-runtime-library/reference/alloca.md) 函数置于将捕获堆栈溢出的[除 try 语句](../../cpp/try-except-statement.md)中。

## <a name="example"></a>示例

下面的代码示例在循环中调用 `MyFunction` ，并且 `MyFunction` 调用 `_alloca` 函数。 `__forceinline` 修饰符导致 `_alloca` 函数内联扩展。

```cpp
// c4750.cpp
// compile with: /O2 /W1 /c
#include <intrin.h>

char * volatile newstr;

__forceinline void myFunction(void) // C4750 warning
{
// The _alloca function does not require a __try/__except
// block because the example uses compiler option /c.
    newstr = (char * volatile) _alloca(1000);
}

int main(void)
{
    for (int i=0; i<50000; i++)
       myFunction();
    return 0;
}
```

## <a name="see-also"></a>另请参阅

[_alloca](../../c-runtime-library/reference/alloca.md)
