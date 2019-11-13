---
title: 编译器警告（等级 1）C4750
ms.date: 11/04/2016
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 35b57cf88bf9f9a170a05af890632316b7030838
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052403"
---
# <a name="compiler-warning-level-1-c4750"></a>编译器警告（等级 1）C4750

“identifier”：函数 with _alloca() 内嵌到循环中

“identifier”函数在循环内强制进行 [_alloca](../../c-runtime-library/reference/alloca.md) 函数的内联扩展，这在执行此循环时会引起堆栈溢出。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保“identifier”函数未使用 [__forceinline](../../cpp/inline-functions-cpp.md) 说明符进行修改。

1. 确保“identifier”函数不包含内含在循环中的函数 [_alloca](../../c-runtime-library/reference/alloca.md) 。

1. 不要指定 [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)、 [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)、 [/Ox](../../build/reference/ox-full-optimization.md)或 [/Og](../../build/reference/og-global-optimizations.md) 编译开关。

1. 请将 [_alloca](../../c-runtime-library/reference/alloca.md) 函数置于会捕获堆栈溢出的 [try-except 语句](../../cpp/try-except-statement.md) 。

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

## <a name="see-also"></a>请参阅

[_alloca](../../c-runtime-library/reference/alloca.md)