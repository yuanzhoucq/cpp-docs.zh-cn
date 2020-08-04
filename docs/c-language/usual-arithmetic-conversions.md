---
title: 常用算术转换
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
ms.openlocfilehash: 7e28c8a234ff840a16228416720ac48763fccc76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231411"
---
# <a name="usual-arithmetic-conversions"></a>常用算术转换

大多数 C 运算符执行类型转换以将表达式的操作数引入常见类型或将较短的值扩展到计算机运算中使用的整数大小。 C 运算符执行的转换取决于特定的运算符和操作数的类型。 但是，许多运算符对整型和浮点型的操作数执行相似的转换。 这些转换称为“算术转换”。 从操作数值到兼容类型的转换会导致不改变其值。

以下汇总的算术转换称为“常用算术转换”。 这些步骤仅应用于需要算术类型的二元运算符。 目的是为了产生常见类型（它也是结果的类型）。 若要确定实际执行的转换，编译器可将以下算法应用于表达式中的二元运算。 下面的步骤不具有优先级。

1. 如果其中一个操作数的类型为 `long double`，则另一个操作数被转换为 `long double` 类型。

1. 如果上述一个条件不满足，且其中一个操作数的类型为 `double`，则另一个操作数被转换为 `double` 类型。

1. 如果上述两个条件不满足，且其中一个操作数的类型为 `float` 类型，则另一个操作数被转换为 `float` 类型。

1. 如果未满足上述三个条件（所有操作数都不是浮点型），则对操作数执行整型转换，如下所示：

   - 如果其中一个操作数的类型为 `unsigned long`，则另一个操作数被转换为 `unsigned long` 类型。

   - 如果上述一个条件不满足，且其中一个操作数的类型为 `long` 类型，另一个操作数的类型为 `unsigned int`，则这两个操作数都被转换为 `unsigned long` 类型。

   - 如果上述两个条件不满足，且其中一个操作数的类型为 `long`，则另一个操作数被转换为 `long` 类型。

   - 如果上述三个条件不满足，且其中一个操作数的类型为 `unsigned int`，则另一个操作数被转换为 `unsigned int` 类型。

   - 如果上述任何条件都不满足，则这两个操作数都被转换为 `int` 类型。

以下代码阐释了这些转换规则：

```
float   fVal;
double  dVal;
int   iVal;
unsigned long ulVal;

dVal = iVal * ulVal; /* iVal converted to unsigned long
                      * Uses step 4.
                      * Result of multiplication converted to double
                      */
dVal = ulVal + fVal; /* ulVal converted to float
                      * Uses step 3.
                      * Result of addition converted to double
                      */
```

## <a name="see-also"></a>请参阅

[C 运算符](../c-language/c-operators.md)
