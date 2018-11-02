---
title: _ReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 01916a9306faa4159f54225b745fd56c35b5ae16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641778"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Microsoft 专用

`_ReturnAddress`内部函数提供了将控件返回给调用方后执行在调用函数中指令的地址。

生成以下程序和通过它在调试器中的步骤。 在逐步执行程序，请注意从返回的地址`_ReturnAddress`。 然后，从函数返回后立即其中`_ReturnAddress`已使用，打开[如何： 使用反汇编窗口](/visualstudio/debugger/how-to-use-the-disassembly-window)并记下要执行的下一个指令的地址匹配从返回的地址`_ReturnAddress`.

优化如内联可能会影响返回的地址。 例如，如果使用编译下面的示例程序[/ob1](../build/reference/ob-inline-function-expansion.md)，`inline_func`将内联到调用函数， `main`。 因此，对调用`_ReturnAddress`从`inline_func`和`main`将每个生成相同的值。

当`_ReturnAddress`编译的程序中使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)，函数包含`_ReturnAddress`调用将编译为本机函数。 当函数编译为托管函数包含调用`_ReturnAddress`，`_ReturnAddress`可能会发生意外行为。

## <a name="requirements"></a>要求

**标头文件** \<intrin.h >

## <a name="example"></a>示例

```
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)