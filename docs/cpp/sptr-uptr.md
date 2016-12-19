---
title: "__sptr、__uptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__uptr_cpp"
  - "__sptr"
  - "__uptr"
  - "__sptr_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__sptr 修饰符"
  - "__uptr 修饰符"
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __sptr、__uptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 在 32 位指针声明上使用 `__sptr` 或 `__uptr` 修饰符以指定编译器如何将 32 位指针转换为 64 位指针。  例如，在将 32 位指针分配给 64 位指针变量或在 64 位平台上取消引用 64 位指针时，将转换该指针。  
  
 为 64 位平台提供支持的 Microsoft 文档有时将 32 位指针的最高有效位用作符号位。  默认情况下，编译器使用符号扩展来将 32 位指针转换为 64 位指针。  即，将 64 位指针的最低有效 32 位设置为 32 位指针的值，并将最高有效 32 位设置为 32 位指针的符号位的值。  如果符号位为 0，则此转换会生成正确的结果；如果符号位为 1，则此转换不会生成正确的结果。  例如，32 位地址 0x7FFFFFFF 生成等效的 64 位地址 0x000000007FFFFFFF，但 32 位地址 0x80000000 未正确地更改为 0xFFFFFFFF80000000。  
  
 `__sptr` 或带符号的指针修饰符指定指针转换将 64 位指针的最高有效位设置为 32 位指针的符号位。  `__uptr` 或不带符号的指针修饰符指定转换将最高有效位设置为零。  下面的声明显示用于两个非限定指针的 `__sptr` 和 `__uptr` 修饰符、两个使用 [\_\_ptr32](../cpp/ptr32-ptr64.md) 类型限定的指针和一个函数参数。  
  
```  
int * __sptr psp;  
int * __uptr pup;  
int * __ptr32 __sptr psp32;  
int * __ptr32 __uptr pup32;  
void MyFunction(char * __uptr __ptr32 myValue);  
```  
  
 将 `__sptr` 和 `__uptr` 修饰符用于指针声明。  在[指针类型限定符](../c-language/pointer-declarations.md)的位置使用修饰符，这意味着修饰符必须在星号的后面。  无法将修饰符用于[指向成员的指针](../cpp/pointers-to-members.md)。  修饰符不影响非指针声明。  
  
 如果不使用 `__sptr` 或 `__uptr` 修饰符，并且您启用[编译器警告（等级 2）C4826](../error-messages/compiler-warnings/compiler-warning-level-2-c4826.md)，则编译器将在将 32 位指针转换为 64 位时发出警告。  
  
## 示例  
 下面的示例声明使用 `__sptr` 和 `__uptr` 修饰符的 32 位指针，将每个 32 位指针分配给 64 位指针变量，然后显示每个 64 位指针的十六进制值。  该示例利用本机 64 位编译器进行编译并在 64 位平台上执行。  
  
```  
// sptr_uptr.cpp  
// processor: x64  
#include "stdio.h"  
  
// Warning C4826 is off by default.  
  
int main()  
{  
    void *        __ptr64 p64;  
    void *        __ptr32 p32d; //default signed pointer  
    void * __sptr __ptr32 p32s; //explicit signed pointer  
    void * __uptr __ptr32 p32u; //explicit unsigned pointer  
  
// Set the 32-bit pointers to a value whose sign bit is 1.  
    p32d = reinterpret_cast<void *>(0x87654321);  
    p32s = p32d;  
    p32u = p32d;  
  
// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated   
// to the __sptr and __uptr modifiers.   
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");  
    printf("p32d:       %p\n", p32d);   
    printf("p32s:       %p\n", p32s);  
    printf("p32u:       %p\n", p32u);  
  
    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");  
    p64 = p32d;   
    printf("p32d: p64 = %p\n", p64);  
    p64 = p32s;  
    printf("p32s: p64 = %p\n", p64);  
    p64 = p32u;  
    printf("p32u: p64 = %p\n", p64);  
    return 0;  
}  
```  
  
  **显示每个 32 位指针（作为无符号的 64 位指针）：**  
**p32d:       0000000087654321**  
**p32s:       0000000087654321**  
**p32u:       0000000087654321**  
**显示从每个 32 位指针创建的 64 位指针：**  
**p32d: p64 \= FFFFFFFF87654321**  
**p32s: p64 \= FFFFFFFF87654321**  
**p32u: p64 \= 0000000087654321**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)