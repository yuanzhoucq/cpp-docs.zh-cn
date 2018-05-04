---
title: __int8、 __int16、 __int32、 __int64 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
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
ms.openlocfilehash: 8083d37d2526820ccd75104f9ee8a748eb5d33bc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="int8-int16-int32-int64"></a>__int8、__int16、__int32、__int64
## <a name="microsoft-specific"></a>Microsoft 专用  
 Microsoft C/C++ 功能支持固定大小整数类型。 可以通过使用声明 8 位、 16、 32 位或 64 位整数变量 **__int * * * n*类型说明符，其中*n*是 8、 16、 32 或 64。  
  
 以下示例为这些类型的固定大小整数声明了一个变量：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 `__int8`、`__int16` 和 `__int32` 类型是大小相同的 ANSI 类型的同义词，用于编写在多个平台中具有相同行为的可移植代码。 `__int8`数据类型是类型的同义词， `char`，`__int16`是类型的同义词，**短**，和`__int32`是类型的同义词， `int`。 `__int64`类型是类型的同义词， `long long`。  
  
## <a name="example"></a>示例  
 下面的示例说明 __int*xx*参数将被提升为`int`:  
  
```  
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
 [关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)   
 [数据类型范围](../cpp/data-type-ranges.md)