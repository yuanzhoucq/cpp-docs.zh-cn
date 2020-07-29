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
ms.openlocfilehash: 7888a282fffbaa2a23783c3875e02838fd0b1826
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227395"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8、__int16、__int32、__int64

**Microsoft 专用**

Microsoft C/C++ 功能支持固定大小整数类型。 可以使用类型说明符声明8、16、32或64位整数变量 **`__intN`** ，其中， ***`N`*** 为8、16、32或64。

以下示例为这些类型的固定大小整数声明了一个变量：

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

类型 **`__int8`** 、 **`__int16`** 和 **`__int32`** 是大小相同的 ANSI 类型的同义词，用于编写在多个平台上行为相同的可移植代码。 **`__int8`** 数据类型与类型同义，与 **`char`** **`__int16`** 类型同义， **`short`** 并且 **`__int32`** 与类型同义 **`int`** 。 **`__int64`** 类型与类型的同义词 **`long long`** 。

为了与早期版本兼容， **`_int8`** 、、和 **`_int16`** **`_int32`** **`_int64`** 是指定了、、和的同义词 **`__int8`** ， **`__int16`** **`__int32`** **`__int64`** 除非指定编译器选项 " [ `/Za` \( 禁用语言扩展](../build/reference/za-ze-disable-language-extensions.md)"。

## <a name="example"></a>示例

下面的示例演示 `__intN` 参数将提升为 **`int`** ：

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

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[内置类型](../cpp/fundamental-types-cpp.md)<br/>
[数据类型范围](../cpp/data-type-ranges.md)<br/>
