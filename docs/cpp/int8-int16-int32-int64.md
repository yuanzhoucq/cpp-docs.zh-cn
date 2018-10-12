---
title: __int8，__int16，__int32，__int64 |Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
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
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b639e7a65bbe206d029a5ba28109170cb0f6a610
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163538"
---
# <a name="int8-int16-int32-int64"></a>__int8、__int16、__int32、__int64

**Microsoft 专用**

Microsoft C/C++ 功能支持固定大小整数类型。 可以通过使用声明 8 位、 16 位、 32 位或 64 位整数变量 **__int**<em>n</em>类型说明符，其中*n*是 8、 16、 32 或 64。

以下示例为这些类型的固定大小整数声明了一个变量：

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

类型 **__int8**， **__int16**，并 **__int32**是同义词，具有相同的 ANSI 类型的大小，并可用于编写的行为相同的可移植代码跨多个平台。 **__Int8**数据类型是同义词，具有类型**char**， **__int16**是类型的同义词**短**，和 **__int32**是类型的同义词**int**。**__Int64**类型是同义词，具有类型**超长**。

与以前版本的兼容性 **_int8**， **_int16**， **_int32**，以及 **_int64**是同义词的 **__int8**， **__int16**， **__int32**，并且 **__int64**除非编译器选项[/Za\(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)指定。

## <a name="example"></a>示例

下面的示例说明 __int*xx*参数将提升为**int**:

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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[基本类型](../cpp/fundamental-types-cpp.md)<br/>
[数据类型范围](../cpp/data-type-ranges.md)<br/>
