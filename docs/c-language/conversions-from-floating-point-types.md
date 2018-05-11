---
title: 从浮点类型的转换 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce86a9ceffaa5d9dacfe56e6b89b677b3abb1517
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="conversions-from-floating-point-types"></a>从浮点类型的转换

转换为 double 或 long double 的 float 值，或转换为 long double 的 double 值不会发生更改。 如果可能，请准确表示转换为 float 值的 double 值。 如果无法准确表示该值，则可能会丢失精度。 如果结果超出范围，则该行为是不确定的。 有关浮点类型的范围，请参阅[浮点常量的限制](../c-language/limits-on-floating-point-constants.md)。

通过以下方式将浮点值转换为整数值：先将其浮点值转换为 long，然后从 long 值转换为特定整数值。 浮点值的小数部分在转换为 long 的过程中将被丢弃。 如果结果仍过大而无法放入 long，则转换的结果是不确定的。

**Microsoft 专用**

在将 double 或 long double 浮点数转换为更小的浮点数时，如果发生下溢，则浮点变量的值将向零截断。 溢出会导致出现运行时错误。 请注意，Microsoft C 编译器会将 long double 映射到类型 double。

**结束 Microsoft 专用**

下表汇总了来自浮点型的转换。

## <a name="conversions-from-floating-point-types"></a>从浮点类型的转换

|From|到|方法|
|----------|--------|------------|
|**float**|**char**|转换为 long；将 long 转换为 char|
|**float**|**short**|转换为 long；将 long 转换为 short|
|**float**|**long**|在小数点处截断。 如果结果过大而无法表示为 long，则结果是不确定的。|
|**float**|**unsigned short**|转换为 long；将 long 转换为 unsigned short|
|**float**|**unsigned long**|转换为 long；将 long 转换为 unsigned long|
|**float**|**double**|更改内部表示形式|
|**float**|**long double**|更改内部表示形式|
|**double**|**char**|转换为 float；将 float 转换为 char|
|**double**|**short**|转换为 float；将 float 转换为 short|
|**double**|**long**|在小数点处截断。 如果结果过大而无法表示为 long，则结果是不确定的。|
|**double**|**unsigned short**|转换为 long；将 long 转换为 unsigned short|
|**double**|**unsigned long**|转换为 long；将 long 转换为 unsigned long|
|**double**|**float**|表示为 float。 如果 double 值不能正确表示为 float，则会丢失精度。 如果值太大而无法表示为 float，则结果是不确定的。|
|**long double**|**char**|转换为 float；将 float 转换为 char|
|**long double**|**short**|转换为 float；将 float 转换为 short|
|**long double**|**long**|在小数点处截断。 如果结果过大而无法表示为 long，则结果是不确定的。|
|**long double**|**unsigned short**|转换为 long；将 long 转换为 unsigned short|
|**long double**|**unsigned long**|转换为 long；将 long 转换为 unsigned long|
|**long double**|**float**|表示为 float。 如果 double 值不能正确表示为 float，则会丢失精度。 如果值太大而无法表示为 float，则结果是不确定的。|
|**long double**|**double**|long double 值被视为 double。|

如果要转换的值大于最大正 long 值，则从 float、double 或 long double 值到 unsigned long 的转换就是不准确的。

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)  
