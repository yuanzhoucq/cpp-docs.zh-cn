---
title: "为何浮点数可能丢失精度 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DBL_EPSILON 常量"
  - "浮点数字, 精度"
  - "FLT_EPSILON 常量"
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 为何浮点数可能丢失精度
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

浮点十进制值通常没有完全相同的二进制表示形式。  这是 CPU 所采用的浮点数据表示形式的副作用。  为此，可能会经历一些精度丢失，并且一些浮点运算可能会产生意外的结果。  
  
 导致此行为的原因是下面之一：  
  
-   十进制数的二进制表示形式可能不精确。  
  
-   使用的数字之间类型不匹配（例如，混合使用浮点型和双精度型）。  
  
 为解决此行为，大多数程序员或是确保值比需要的大或者小，或是获取并使用可以维护精度的二进制编码的十进制 \(BCD\) 库。  
  
 浮点值的二进制表示形式影响浮点计算的精度和准确性。  Microsoft Visual C\+\+ 使用 [IEEE 浮点格式](../../build/reference/ieee-floating-point-representation.md)。  
  
## 示例  
  
```  
// Floating-point_number_precision.c  
// Compile options needed: none. Value of c is printed with a decimal   
// point precision of 10 and 6 (printf rounded value by default) to   
// show the difference  
#include <stdio.h>  
  
#define EPSILON 0.0001   // Define your own tolerance  
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))  
  
int main() {  
   float a, b, c;  
  
   a = 1.345f;  
   b = 1.123f;  
   c = a + b;  
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result  
   if (c == 2.468)            // Comment this line for correct result  
      printf_s("They are equal.\n");  
   else  
      printf_s("They are not equal! The value of c is %13.10f "  
                "or %f",c,c);  
}  
```  
  
  **它们并不相等！  c 的值为 2.4679999352 或 2.468000。**    
## 注释  
 对于 EPSILON，可以使用常量 FLT\_EPSILON（对于浮点型定义为 1.192092896e\-07F）或者 DBL\_EPSILON（对于双精度型定义为 2.2204460492503131e\-016）。  需要为这些常量包含 float.h。  这些常数被定义为最小的正数 x，因此 x\+1.0 不等于 1.0。  因为这是非常小的数，所以对于涉及大数的计算应采用用户定义的公差。  
  
## 请参阅  
 [优化代码](../../build/reference/optimizing-your-code.md)