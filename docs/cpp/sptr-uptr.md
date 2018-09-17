---
title: __sptr、 __uptr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __uptr_cpp
- __sptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc6625e9f9137bc6adbe10270ef7192d2f1672f0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700851"
---
# <a name="sptr-uptr"></a>__sptr、__uptr
**Microsoft 专用**

 使用 **__sptr**或 **__uptr**修饰符来指定编译器如何将 32 位指针转换为 64 位指针在 32 位指针声明。 例如，在将 32 位指针分配给 64 位指针变量或在 64 位平台上取消引用 64 位指针时，将转换该指针。  
  
 为 64 位平台提供支持的 Microsoft 文档有时将 32 位指针的最高有效位用作符号位。 默认情况下，编译器使用符号扩展来将 32 位指针转换为 64 位指针。 即，将 64 位指针的最低有效 32 位设置为 32 位指针的值，并将最高有效 32 位设置为 32 位指针的符号位的值。 如果符号位为 0，则此转换会生成正确的结果；如果符号位为 1，则此转换不会生成正确的结果。 例如，32 位地址 0x7FFFFFFF 生成等效的 64 位地址 0x000000007FFFFFFF，但 32 位地址 0x80000000 未正确地更改为 0xFFFFFFFF80000000。  
  
 **__Sptr**，或带符号的指针修饰符指定指针转换将 64 位指针的最高有效位设置为 32 位指针的符号位。 **__Uptr**，或无符号的指针修饰符指定转换将设置为零的最高有效位。 下面的声明显示 **__sptr**并 **__uptr**修饰符与两个非限定指针一起使用，用两个指针的限定[__ptr32](../cpp/ptr32-ptr64.md)类型和函数参数。  
  
```cpp 
int * __sptr psp;  
int * __uptr pup;  
int * __ptr32 __sptr psp32;  
int * __ptr32 __uptr pup32;  
void MyFunction(char * __uptr __ptr32 myValue);  
```  
  
 使用 **__sptr**并 **__uptr**修饰符用于指针声明。 中的位置使用修饰符[指针类型限定符](../c-language/pointer-declarations.md)，这意味着修饰符必须在星号的后面。 不能使用修饰符用于[指向成员的指针](../cpp/pointers-to-members.md)。 修饰符不影响非指针声明。  
  
## <a name="example"></a>示例  
 下面的示例将使用的 32 位指针声明 **__sptr**并 **__uptr**修饰符，将每个 32 位指针分配给 64 位指针变量，并显示每个 64-的十六进制值位指针。 该示例利用本机 64 位编译器进行编译并在 64 位平台上执行。  
  
```cpp  
// sptr_uptr.cpp  
// processor: x64  
#include "stdio.h"  
  
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
  
```Output  
Display each 32-bit pointer (as an unsigned 64-bit pointer):  
p32d:       0000000087654321  
p32s:       0000000087654321  
p32u:       0000000087654321  
  
Display the 64-bit pointer created from each 32-bit pointer:  
p32d: p64 = FFFFFFFF87654321  
p32s: p64 = FFFFFFFF87654321  
p32u: p64 = 0000000087654321  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)