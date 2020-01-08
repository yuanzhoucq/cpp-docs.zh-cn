---
title: __int8、__int16、__int32、__int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 4e793f23581f7dc62a39fcd8c5c504fb5a2ccbc9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301465"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8、__int16、__int32、__int64

**Microsoft 专用**

Microsoft C/C++ 功能支持固定大小整数类型。 您可以使用 **__int**<em>n</em>类型说明符声明8、16、32或64位整数变量，其中*n*为8、16、32或64。

以下示例为这些类型的固定大小整数声明了一个变量：

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

**__Int8**、 **__int16**和 **__int32**的类型是大小相同的 ANSI 类型的同义词，用于编写在多个平台上表现完全相同的可移植代码。 **__Int8**的数据类型与类型**char**同义， **__int16**是类型为**short**的同义词， **__int32**与**int**类型是同义词。 **__Int64**类型是**long**类型的同义词。

为了与早期版本兼容， **_int8**、 **_int16**、 **_int32**和 **_int64**是 **__int8**、 **__int16**、 **__int32**和 **__int64**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="example"></a>示例

下面的示例说明 __int*xx*参数将提升为**int**：

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[内置类型](../cpp/fundamental-types-cpp.md)<br/>
[数据类型范围](../cpp/data-type-ranges.md)<br/>
