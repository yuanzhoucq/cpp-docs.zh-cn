---
title: __sptr、__uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: bfa468c96196c417415801239925707c43a49c4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178673"
---
# <a name="__sptr-__uptr"></a>__sptr、__uptr

**Microsoft 专用**

使用32位指针声明上的 **__sptr**或 **__uptr**修饰符来指定编译器如何将32位指针转换为64位指针。 例如，在将 32 位指针分配给 64 位指针变量或在 64 位平台上取消引用 64 位指针时，将转换该指针。

为 64 位平台提供支持的 Microsoft 文档有时将 32 位指针的最高有效位用作符号位。 默认情况下，编译器使用符号扩展来将 32 位指针转换为 64 位指针。 即，将 64 位指针的最低有效 32 位设置为 32 位指针的值，并将最高有效 32 位设置为 32 位指针的符号位的值。 如果符号位为 0，则此转换会生成正确的结果；如果符号位为 1，则此转换不会生成正确的结果。 例如，32 位地址 0x7FFFFFFF 生成等效的 64 位地址 0x000000007FFFFFFF，但 32 位地址 0x80000000 未正确地更改为 0xFFFFFFFF80000000。

**__Sptr**或带符号的指针修饰符指定指针转换将64位指针的最高有效位设置为32位指针的符号位。 **__Uptr**或未签名的指针修饰符指定转换将最高有效位设置为零。 以下声明显示了用于两个非限定指针的 **__sptr**和 **__uptr**修饰符，两个用[__ptr32](../cpp/ptr32-ptr64.md)类型限定的指针和一个函数参数。

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

使用带有指针声明的 **__sptr**和 **__uptr**修饰符。 在[指针类型限定符](../c-language/pointer-declarations.md)的位置使用修饰符，这意味着修饰符必须位于星号之后。 不能将修饰符用于[指向成员的指针](../cpp/pointers-to-members.md)。 修饰符不影响非指针声明。

为了与早期版本兼容， **_sptr**和 **_uptr**是 **__sptr**和 **__uptr**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="example"></a>示例

下面的示例声明了32位指针，该指针使用 **__sptr**和 **__uptr**修饰符，将每个32位指针分配给64位指针变量，然后显示每个64位指针的十六进制值。 该示例利用本机 64 位编译器进行编译并在 64 位平台上执行。

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

## <a name="see-also"></a>另请参阅

[Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)
