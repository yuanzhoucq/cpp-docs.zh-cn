---
title: "_AddressOfReturnAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_AddressOfReturnAddress_cpp"
  - "_AddressOfReturnAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AddressOfReturnAddress 指令"
  - "AddressOfReturnAddress 指令"
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _AddressOfReturnAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 提供包含该函数的返回地址内存位置的地址。  此地址不可用于访问其他内存位置 \(例如，函数的参数\)。  
  
## 语法  
  
```  
void * _AddressOfReturnAddress();  
```  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`_AddressOfReturnAddress`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 当 `_AddressOfReturnAddress` 程序中使用编译 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)时，包含 `_AddressOfReturnAddress` 的函数调用编译为本机函数。  当为管理编译函数调用到包含 `_AddressOfReturnAddress`时的函数， `_AddressOfReturnAddress` 可能与预期的方式工作。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// compiler_intrinsics_AddressOfReturnAddress.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
// This function will print three values:  
//   (1) The address retrieved from _AddressOfReturnAdress  
//   (2) The return address stored at the location returned in (1)  
//   (3) The return address retrieved the _ReturnAddress* intrinsic  
// Note that (2) and (3) should be the same address.  
__declspec(noinline)  
void func() {  
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();  
   printf_s("%p\n", pvAddressOfReturnAddress);  
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));  
   printf_s("%p\n", _ReturnAddress());  
}  
  
int main() {  
   func();  
}  
```  
  
  **0012FF78**  
**00401058**  
**00401058**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)