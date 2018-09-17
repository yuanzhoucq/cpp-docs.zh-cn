---
title: 为何浮点数可能丢失精度 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de54610676ade49f7ce41e00ed0049b20e46709c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700002"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>为何浮点数可能丢失精度

浮点十进制值通常没有准确的二进制表示形式。 这是 CPU 表示的浮点型数据的方式的副作用。 出于此原因，可能会遇到一些丢失精度，并且某些浮点操作可能产生意外的结果。

此行为是以下其中一个的结果：

- 可能不是精确的十进制数的二进制表示形式。

- 所使用的数字 （例如，混合 float 和 double） 之间没有类型不匹配。

若要解决此问题，大多数程序员或是确保的值大于或小于什么需要或他们获取并使用可以维护精度的二进制编码的十进制 (BCD) 库。

浮点值的二进制表示形式会影响精度和浮点计算的准确性。 使用 Microsoft Visual c + + [IEEE 浮点格式](../../build/reference/ieee-floating-point-representation.md)。

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

对于 EPSILON，你可以使用常量 FLT_EPSILON，定义的浮点型作为 1.192092896e-07F，或 DBL_EPSILON，定义表示双精度作为 2.2204460492503131e-016。 需要包含这些常量的 float.h。 这些常数被定义为最小正数 x 号，例如 x + 1.0 不等于 1.0。 由于这是极小的数字，您应使用用户定义涉及大量计算的容错能力。

## <a name="see-also"></a>请参阅

[优化代码](../../build/reference/optimizing-your-code.md)