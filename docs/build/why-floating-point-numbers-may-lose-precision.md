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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298709"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>为何浮点数可能丢失精度

浮点十进制值通常没有完全相同的二进制表示形式。 这是 CPU 表示浮点数据的方式的副作用。 出于此原因，你可能会遇到一些精度损失，并且某些浮点运算可能会产生意外的结果。

此行为是下列其中一项的结果：

- 十进制数的二进制表示形式不能是精确的。

- 使用的数字之间存在类型不匹配（例如，混合 float 和 double）。

若要解决此问题，大多数程序员要么确保该值大于或小于所需值，要么获取并使用二进制编码的十进制（BCD）库来保持精度。

浮点值的二进制表示形式会影响浮点计算的精度和准确性。 Microsoft 视觉C++对象使用[IEEE 浮点格式](ieee-floating-point-representation.md)。

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

## <a name="comments"></a>Comments

对于 EPSILON，可以使用 FLT_EPSILON 的常量，该常量定义为 float 作为 1.192092896 e-07F 或 DBL_EPSILON，后者定义为 double as 2.2204460492503131 e-016。 需要为这些常量包含 float。 这些常量定义为最小正数 x，因此 x + 1.0 不等于1.0。 由于这是一个非常小的数字，因此应将用户定义的公差用于涉及非常大的数字的计算。

## <a name="see-also"></a>另请参阅

[优化代码](optimizing-your-code.md)
