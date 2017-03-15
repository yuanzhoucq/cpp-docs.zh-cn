---
title: "__int8、__int16、__int32、__int64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__int8_cpp"
  - "__int64"
  - "__int8"
  - "__int16"
  - "__int16_cpp"
  - "__int64_cpp"
  - "__int32_cpp"
  - "__int32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__int16 关键字 [C++]"
  - "__int32 关键字 [C++]"
  - "__int64 关键字 [C++]"
  - "__int8 关键字 [C++]"
  - "Integer 数据类型, C++ 中的整型"
  - "整型 [C++]"
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __int8、__int16、__int32、__int64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 Microsoft C\/C\+\+ 功能支持固定大小整数类型。  您可以使用 **\_\_int***n* 类型说明符声明 8 位、16 位、32 位或 64 位整数变量，其中 *n* 为 8、16、32 或 64。  
  
 以下示例为这些类型的固定大小整数声明了一个变量：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 `__int8`、`__int16` 和 `__int32` 类型是大小相同的 ANSI 类型的同义词，用于编写在多个平台中具有相同行为的可移植代码。  `__int8` 数据类型与 `char` 类型是同义词，`__int16` 与 **short** 类型是同义词，而 `__int32` 与 `int` 类型是同义词。  `__int64` 类型没有 ANSI 等效项。  
  
## 示例  
 以下示例说明 \_\_int*xx* 参数将提升为 `int`：  
  
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
  
  **func**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)   
 [数据类型范围](../cpp/data-type-ranges.md)