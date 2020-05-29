---
title: 从浮点类型的转换
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998712"
---
# <a name="conversions-from-floating-point-types"></a>从浮点类型的转换

如果原始值在结果类型中是可精确表示的，则转换为另一种浮点类型的浮点值的值不会发生任何变化。 如果原始值是数值，但不能精确地表示，则结果是下一个更大的可表示值或下一个更小的可表示值。 有关浮点类型的范围，请参阅[浮点常量的限制](../c-language/limits-on-floating-point-constants.md)。

首先通过丢弃任何小数值来截断转换为整型类型的浮点值。 如果这个截断的值在结果类型中是可表示的，那么结果必须是该值。 如果结果值不可表示，结果值是未定义的。

**Microsoft 专用**

Microsoft 编译器对“浮点”值使用 IEEE-754 binary32 表示，对“long double”和“double”使用 binary64 表示    。 由于 long double 和 double 使用相同的表示形式，因此它们具有相同的范围和精度   。

当编译器将“double”或“long double”浮点数转换为“浮点”时，它将根据浮点环境控件四舍五入，该环境控件默认为“舍入到最近值，但绑定到偶数”    。 如果数值过大或过小，无法表示为数值“浮点”值，则根据原始值的符号，转换结果为正无穷或负无穷，如果启用，则引发溢出异常  。

在转换为整数类型时，转换为小于 long 的类型的结果是将值转换为 long，然后转换为结果类型的结果   。

对于转换为至少与“long”一样大的整数类型，如果转换的值太大或太小，无法在结果类型中表示，则可能会返回以下任何值  ：

- 结果可能是一个标记值，它是离零最远的可表示值  。 对于有符号类型，它是最小的可表示值 (0x800...0)。 对于无符号类型，它是最大的可表示值 (0xFF...F)。

- 结果可能是饱和值，其中过大的值被转换为最大的可表示值，过小的值被转换为最小的可表示值  。 这两个值中的一个也用作标记值。

- 对于转换到“unsigned long”或“unsigned long long”，转换范围外的值的结果可能不是最大或最小可表示值   。 结果是标记值还是饱和值取决于编译器选项和目标体系结构。 将来的编译器版本可能会返回一个饱和值或标记值。

**结束 Microsoft 专用**

下表汇总了来自浮点型的转换。

## <a name="table-of-conversions-from-floating-point-types"></a>浮点类型转换表

|From|功能|方法|
|----------|--------|------------|
|**float**|**char**|转换为 long；将 long 转换为 char   |
|**float**|**short**|转换为 long  ；将 long  转换为  short|
|**float**|**int**|在小数点处截断。 如果结果过大而无法表示为 int，则结果是不确定的  。|
|**float**|**long**|在小数点处截断。 如果结果过大而无法表示为 long  ，则结果是不确定的。|
|**float**|**long long**|在小数点处截断。 如果结果过大而无法表示为“long long”，则结果是不确定的  。|
|**float**|**unsigned char**|转换为 long；将 long 转换为 unsigned char   |
|**float**|**unsigned short**|转换为 long  ；将 long  转换为  unsigned short|
|**float**|**unsigned**|在小数点处截断。 如果结果过大而无法表示为 unsigned，则结果是不确定的  。|
|**float**|**unsigned long**|在小数点处截断。 如果结果过大而无法表示为 unsigned long，则结果是不确定的  。|
|**float**|**unsigned long long**|在小数点处截断。 如果结果过大而无法表示为 unsigned long long，则结果是不确定的  。|
|**float**|**double**|表示为 double  。|
|**float**|**long double**|表示为 long double  。|
|**double**|**char**|转换为 float；将 float 转换为 char   |
|**double**|**short**|转换为 float  ；将 float  转换为  short|
|**double**|**int**|在小数点处截断。 如果结果过大而无法表示为 int，则结果是不确定的  。|
|**double**|**long**|在小数点处截断。 如果结果过大而无法表示为 long  ，则结果是不确定的。|
|**double**|**unsigned char**|转换为 long；将 long 转换为 unsigned char   |
|**double**|**unsigned short**|转换为 long  ；将 long  转换为  unsigned short|
|**double**|**unsigned**|在小数点处截断。 如果结果过大而无法表示为 unsigned，则结果是不确定的  。|
|**double**|**unsigned long**|在小数点处截断。 如果结果过大而无法表示为 unsigned long，则结果是不确定的  。|
|**double**|**unsigned long long**|在小数点处截断。 如果结果过大而无法表示为 unsigned long long，则结果是不确定的  。|
|**double**|**float**|表示为  float。 如果 double 值不能正确表示为 float，则会丢失精度   。 如果值太大而无法表示为 float  ，则结果是不确定的。|
|**double**|**long double**| long double 值被视为 double  。|

从 long double 的转换遵循与从 double 的转换相同的方法   。

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
