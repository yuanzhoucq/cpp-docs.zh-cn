---
title: 从浮点类型的转换
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998712"
---
# <a name="conversions-from-floating-point-types"></a>从浮点类型的转换

如果原始值完全在结果类型中表示形式，则转换为另一个浮点类型的浮点值不会发生更改。 如果原始值是数值，但并不完全表示，则结果是下一个较大或较低的可表示值。 有关浮点类型的范围，请参阅[浮点常量的限制](../c-language/limits-on-floating-point-constants.md)。

首先，通过丢弃任何小数值来截断转换为整型的浮点值。 如果此截断值可在结果类型中表示，则结果必须为该值。 如果它不是可表示的，则结果值为 undefined。

**Microsoft 专用**

Microsoft 编译器对**float**值使用 IEEE-754 binary32 表示形式，将 binary64 表示形式用于**长双精度**和**双精度**。 由于**长双精度**和**双**精度值使用相同的表示形式，因此它们具有相同的范围和精度。

当编译器将**double**或**long double**浮点数转换为**float**时，它会根据浮点环境控件舍入结果，默认值为 "舍入到最接近的值"。 如果数字值太大或太低而无法表示为数值**浮点**值，则转换结果为正或负无穷大（根据原始值的符号），如果已启用，则会引发溢出异常。

转换为整数类型时，转换为小于**long**类型的结果是将值转换为**long**，然后转换为结果类型的结果。

若要转换到整数类型，该类型的值应小于或等于结果类型，如果转换的值太大或过**低，则**可能会返回以下任何值：

- 结果可能是一个*sentinel 值*，它是最远于零的可表示值。 对于有符号类型，它是最小的可表示值（0x800）。0）。 对于无符号类型，它是可表示的最大值（0xFF .。。F）。

- 结果可能是*饱和*的，其中的值太大而无法表示转换为最大的可表示值，并且值太低而无法表示转换为最小的可表示值。 这两个值中的一个值还用作 sentinel 值。

- 若要转换为**无符号**长或**无符号长**时间，转换超出范围的值的结果可能是一个值，而不是最高或最低的可表示值。 结果是 sentinel 还是饱和值取决于编译器选项和目标体系结构。 未来的编译器版本可能改为返回一个饱和或 sentinel 值。

**结束 Microsoft 专用**

下表汇总了来自浮点型的转换。

## <a name="table-of-conversions-from-floating-point-types"></a>浮点类型转换表

|From|功能|方法|
|----------|--------|------------|
|**float**|**char**|转换为 long；将 long 转换为 char|
|**float**|**short**|转换为 long；将 long 转换为short|
|**float**|**int**|在小数点处截断。 如果 result 太大而无法表示为**int**，则结果是不确定的。|
|**float**|**long**|在小数点处截断。 如果结果过大而无法表示为 long，则结果是不确定的。|
|**float**|**long long**|在小数点处截断。 如果 result 太大而无法表示为**长**时间，则结果是不确定的。|
|**float**|**unsigned char**|转换为**long**;将**long**转换为**无符号字符**|
|**float**|**unsigned short**|转换为 long；将 long 转换为unsigned short|
|**float**|**unsigned**|在小数点处截断。 如果 result 太大而无法表示为**无符号**，则结果是不确定的。|
|**float**|**unsigned long**|在小数点处截断。 如果 result 太大而无法表示为**无符号 long**，则结果是不确定的。|
|**float**|**无符号长长**|在小数点处截断。 如果 result 太大而无法表示为**无符号长**长时间，则结果是不确定的。|
|**float**|**double**|表示为**双精度型**。|
|**float**|**long double**|表示为**长双精度**。|
|**double**|**char**|转换为 float；将 float 转换为 char|
|**double**|**short**|转换为 float；将 float 转换为short|
|**double**|**int**|在小数点处截断。 如果 result 太大而无法表示为**int**，则结果是不确定的。|
|**double**|**long**|在小数点处截断。 如果结果过大而无法表示为 long，则结果是不确定的。|
|**double**|**unsigned char**|转换为**long**;将**long**转换为**无符号字符**|
|**double**|**unsigned short**|转换为 long；将 long 转换为unsigned short|
|**double**|**unsigned**|在小数点处截断。 如果 result 太大而无法表示为**无符号**，则结果是不确定的。|
|**double**|**unsigned long**|在小数点处截断。 如果 result 太大而无法表示为**无符号 long**，则结果是不确定的。|
|**double**|**无符号长长**|在小数点处截断。 如果 result 太大而无法表示为**无符号长**长时间，则结果是不确定的。|
|**double**|**float**|表示为float。 如果**double**值不能精确表示为**float**，则会丢失精度。 如果值太大而无法表示为 float，则结果是不确定的。|
|**double**|**long double**|long double 值被视为 double。|

从**long double**转换后的方法与**双**精度型转换相同。

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
