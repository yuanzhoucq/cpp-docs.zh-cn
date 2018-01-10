---
title: "_ReturnAddress |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _ReturnAddress
dev_langs: C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d207fcba6846d0a5e599d6273f5b35bb554bda40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="returnaddress"></a>_ReturnAddress
## <a name="microsoft-specific"></a>Microsoft 专用  
 `_ReturnAddress`内部函数提供了在将控制权返回给调用方后执行的调用函数中的指令的地址。  
  
 生成以下程序和通过它在调试器中的步骤。 逐步执行程序时，请注意从返回的地址`_ReturnAddress`。 然后，立即在从函数返回其中`_ReturnAddress`已使用，请打开[如何： 使用反汇编窗口](/visualstudio/debugger/how-to-use-the-disassembly-window)并记下要执行的下一个指令的地址与从返回的地址匹配`_ReturnAddress`.  
  
 优化如内联可能会影响的寄信人地址。 例如，如果使用编译下面的示例程序[/Ob1](../build/reference/ob-inline-function-expansion.md)，`inline_func`会到调用的函数、 内联`main`。 因此，对的调用`_ReturnAddress`从`inline_func`和`main`将各自生成相同的值。  
  
 当`_ReturnAddress`在编译的程序中使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)，函数包含`_ReturnAddress`调用将编译为本机函数。 当函数编译为托管调入函数包含`_ReturnAddress`，`_ReturnAddress`可能无法按预期方式正常工作。  
  
## <a name="requirements"></a>惠?  
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
 [_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [关键字](../cpp/keywords-cpp.md)