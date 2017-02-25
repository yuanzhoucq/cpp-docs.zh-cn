---
title: "_ReturnAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ReturnAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ReturnAddress 内部函数"
  - "ReturnAddress 内部函数"
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _ReturnAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 `_ReturnAddress` 内部提供命令的地址在要执行的调用函数的，在控件回调用方之后。  
  
 将生成以下过程和步骤在调试器。  您逐句通过程序，请注意从 `_ReturnAddress`返回的地址。  然后，在从返回 `_ReturnAddress` 使用的功能后，打开 [如何：使用“反汇编”窗口](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md) 并注意下命令的地址是该地址从 `_ReturnAddress`返回已执行的匹配。  
  
 优化 \(例如内联会影响返回地址。  例如，在中，如果下面的示例程序编译 [\/Ob1](../build/reference/ob-inline-function-expansion.md)， `inline_func` 内联到调用函数， `main`。  因此，对从 `inline_func` 的 `_ReturnAddress` ，并 `main` 将每个生成相同的值。  
  
 当 `_ReturnAddress` 程序中使用编译 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)时，包含 `_ReturnAddress` 的函数调用将编译为本机函数。  当为管理编译函数调用到包含 `_ReturnAddress`时的函数， `_ReturnAddress` 可能不会象预期方式工作。  
  
## 要求  
 **头文件** \<intrin.h\>  
  
## 示例  
  
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
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)