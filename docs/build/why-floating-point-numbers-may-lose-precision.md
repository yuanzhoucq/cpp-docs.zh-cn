---
title: 为何浮点数可能丢失精度
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298709"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>为何浮点数可能丢失精度

浮点十进制值通常没有完全相同的二进制表示形式。 这是 CPU 所采用的浮点数据表示形式的副作用。 因此，你可能会遇到一些精度丢失，并且某些浮点运算可能会产生意外的结果。

导致此行为的原因是下面之一：

- 十进制数的二进制表示形式可能不精确。

- 使用的数字之间存在类型不匹配（例如，混合使用浮点和双精度）。

为解决此行为，大多数程序员要么确保值大于或小于所需的值，要么获取并使用可以维护精度的二进制编码的十进制 (BCD) 库。

浮点值的二进制表示形式会影响浮点计算的精度和准确度。 Microsoft Visual C++ 使用 [IEEE 浮点格式](ieee-floating-point-representation.md)。

## <a name="example"></a>示例

```c
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

对于 EPSILON，可以使用常数 FLT_EPSILON（对于浮点型定义为 1.192092896e-07F）或 DBL_EPSILON（对于双精度型定义为 2.2204460492503131e-016）。 对于这些常数，需要包含 float.h。 这些常数定义为最小的正数 x，因此 x+1.0 不等于 1.0。 因为这是一个非常小的数字，所以应对涉及非常大的数字的计算采用用户定义的容差。

## <a name="see-also"></a>请参阅

[优化代码](optimizing-your-code.md)
