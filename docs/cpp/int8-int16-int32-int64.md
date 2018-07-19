---
title: __int8，__int16，__int32，__int64 |Microsoft Docs
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
ms.openlocfilehash: 409197ec99a8df9ad1999b20edd1537f10ced085
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942409"
---
# <a name="int8-int16-int32-int64"></a>__int8、__int16、__int32、__int64
## <a name="microsoft-specific"></a>Microsoft 专用  
 Microsoft C/C++ 功能支持固定大小整数类型。 可以通过使用声明 8 位、 16 位、 32 位或 64 位整数变量 **__int * * * n*类型说明符，其中*n*是 8、 16、 32 或 64。  
  
 以下示例为这些类型的固定大小整数声明了一个变量：  
  
```cpp 
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 类型 **__int8**， **__int16**，并 **__int32**是同义词，具有相同的 ANSI 类型的大小，并可用于编写的行为相同的可移植代码跨多个平台。 **__Int8**数据类型是同义词，具有类型**char**， **__int16**是类型的同义词**短**，和 **__int32**是类型的同义词**int**。**__Int64**类型是同义词，具有类型**超长**。  
  
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
 [关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)   
 [数据类型范围](../cpp/data-type-ranges.md)