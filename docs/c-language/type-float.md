---
title: float 类型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8103ad4054210c7cb3847539f5cdc3f2cebfea6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103823"
---
# <a name="type-float"></a>float 类型

浮点数使用 IEEE（电气和电子工程师协会）格式。 浮点类型的单精度值具有 4 个字节，包括一个符号位、一个 8 位 excess-127 二进制指数和一个 23 位尾数。 尾数表示一个介于 1.0 和 2.0 之间的数。 由于尾数的高顺序位始终为 1，因此它不是以数字形式存储的。 此表示形式为 float 类型提供了一个大约在 3.4E-38 和 3.4E+38 之间的范围。

您可根据应用程序的需求将变量声明为 float 或 double。 这两种类型之间的主要差异在于它们可表示的基数、它们需要的存储以及它们的范围。 下表显示了基数与存储需求之间的关系。

### <a name="floating-point-types"></a>浮点类型

|类型|有效位|字节数|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

浮点变量由尾数（包含数字的值）和指数（包含数字的数量级）表示。

下表显示了分配给每个浮点类型的尾数和指数的位数。 任何 float 或 double 的最高有效位始终是符号位。 如果符号位为 1，则将数字视为负数；否则，将数字视为正数。

### <a name="lengths-of-exponents-and-mantissas"></a>指数和尾数的长度

|类型|指数长度|尾数长度|
|----------|---------------------|---------------------|
|float|8 位|23 位|
|double|11 位|52 位|

由于指数是以无符号形式存储的，因此指数的偏差为其可能值的一半。 对于 float 类型，偏差为 127；对于 double 类型，偏差为 1023。 您可以通过将指数值减去偏差值来计算实际指数值。

存储为二进制分数的尾数大于或等于 1 且小于 2。 对于 float 和 double 类型，最高有效位位置的尾数中有一个隐含的前导 1，这样，尾数实际上分别为 24 和 53 位长，即使最高有效位从未存储在内存中也是如此。

浮点包可以将二进制浮点数存储为非标准化数，而不使用刚刚介绍的存储方法。 “非标准化数”是带有保留指数值的非零浮点数，其中尾数的最高有效位为 0。 通过使用非标准化格式，浮点数的范围可以扩展，但会失去精度。 您无法控制浮点数以标准化形式还是非标准化形式表示；浮点包决定了表示形式。 浮点包从不使用非标准化形式，除非指数变为小于可以标准化形式表示的最小值。

下表显示了可在每种浮点类型的变量中存储的最小值和最大值。 此表中所列的值仅适用于标准化浮点数；非标准化浮点数的最小值更小。 请注意，在 80*x*87 寄存器中保留的数字始终以 80 位标准化形式表示；数字存储在 32 位或 64 位浮点变量（float 类型和 long 类型的变量）中时只能以非标准化形式表示。

### <a name="range-of-floating-point-types"></a>浮点类型的范围

|类型|最小值|最大值|
|----------|-------------------|-------------------|
|浮动|1.175494351 E - 38|3.402823466 E + 38|
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|

如果存储比精度更重要，请考虑对浮点变量使用 float 类型。 相反，如果精度是最重要的条件，则使用 double 类型。

浮点变量可以提升为更大基数的类型（从 float 类型到 double 类型）。 当您对浮点变量执行算术时，通常会出现提升。 此算术始终以与具有最高精度的变量一样高的精度执行。 例如，请考虑下列类型声明：

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

在前面的示例中，变量 `f_short` 提升到类型 double 并且与 `f_long` 相乘；然后，结果舍入到类型 float，然后赋给 `f_short`。

在以下示例中（使用前面示例中的声明），将以浮点（32 位）精度对变量执行算术；结果随后将提升到 double 类型：

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>请参阅

[基本类型的存储](../c-language/storage-of-basic-types.md)