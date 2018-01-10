---
title: "为何浮点数可能丢失精度 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 371aad5dc573a13ca834d8d6d9667a43bb40324e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>为何浮点数可能丢失精度
浮点十进制值通常没有确切的二进制表示形式。 这是如何 CPU 浮点数据表示形式会产生副作用。 为此，你可能会遇到一些丢失精度，和某些浮点运算可能产生意外的结果。  
  
 此行为是下列其中一项的结果：  
  
-   二进制表示形式的十进制数可能不准确。  
  
-   使用的数字 （例如，混合使用 float 和 double） 之间没有类型不匹配。  
  
 若要解决此问题，大多数程序员来说，请确保的值大于或小于什么需要的或它们获取并使用可以维护精度的二进制编码的十进制 (BCD) 库。  
  
 浮点值的二进制表示形式会影响的精度和准确性的浮点计算。 Microsoft Visual c + + 使用[IEEE 浮点格式](../../build/reference/ieee-floating-point-representation.md)。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
They are not equal! The value of c is  2.4679999352 or 2.468000  
```  
  
## <a name="comments"></a>注释  
 对于 EPSILON，你可以使用常量 FLT_EPSILON，定义的浮点型作为 1.192092896e-07F，或 DBL_EPSILON，定义 2.2204460492503131e 作为双精度型-016。 你需要包括这些常量的 float.h。 这些常量定义为最小正数 x 号，例如 x + 1.0 不等于 1.0。 由于这是极小的数字，你应采用对于涉及大量的计算用户定义容差。  
  
## <a name="see-also"></a>请参阅  
 [优化代码](../../build/reference/optimizing-your-code.md)