---
title: 整型
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 0359ef3037a44ed50326d19d1c184c463adcaa5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563574"
---
# <a name="integer-types"></a>整型

根据每个整数常量的值及其表示方式为该常量提供一个类型。 可通过将字母 **l** 或 **L** 追加到任何整数常量的末尾来将该常量强制转换为类型 **long**；可通过将 **u** 或 **U** 追加到该值来将其强制转换为类型 `unsigned`。 小写字母 **l** 会与数字 1 发生混淆，应避免此情况出现。 某些形式的 **long** 整数常量如下所示：

```
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

您分配给常量的类型取决于常量表示的值。 常量的值必须在其类型的可表示值的范围内。 常量的类型用于确定在表达式中使用常量或在应用减号 (**-**) 时执行的转换类型。 此列表汇总了整数常量的转换规则。

- 不带后缀的十进制常量的类型是 `int`、**long int** 或 **unsigned long int**。可用来表示常量值的三种类型中的第一个类型是分配给常量的类型。

- 分配给不带后缀的八进制和十六进制常量的类型是 `int`、`unsigned int`、**long int** 或 **unsigned long int**，具体取决于常量的大小。

- 分配给带 **u** 或 **U** 后缀的常量的类型是 **unsigned int** 或 **unsigned long int**，具体取决于常量的大小。

- 分配给带 **l** 或 **L** 后缀的常量的类型是 **long int** 或 **unsigned long int**，具体取决于常量的大小。

- 分配给带 **u** 或 **U** 后缀的常量和带 **l** 或 **L** 后缀的常量的类型是 **unsigned long int**。

## <a name="see-also"></a>请参阅

[C 整数常量](../c-language/c-integer-constants.md)