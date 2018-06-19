---
title: 从无符号整型类型的转换 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8a77e898feb6676487c557b8e96d54dc793ace
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391517"
---
# <a name="conversions-from-unsigned-integral-types"></a>从无符号整型的转换

通过截断高序位将无符号整数转换为较短的无符号或带符号整数，或者通过零扩展将其转换为一个较长的无符号或带符号整数（请参阅[从无符号整型类型转换](#_clang_table_4..3)表）。

当带整型的值降为较小的带符号整数，或者将无符号整数转换为其相应的带符号整数时，值保持不变（如果可以在新类型中表示该值）。 但是，它表示的值将发生更改（如果设置符号位），如下面的示例所示。

```C
int j;
unsigned short k = 65533;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

如果无法表示它，则结果是实现定义的。 有关 Microsoft C 编译器如何处理整数降级的信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)。 整数转换或对整数进行类型强制会产生相同的行为。

通过某种方式转换无符号值，以便保留其值并使其不直接显示在 C 中。唯一的例外是从 unsigned long 到 float 的转换，这最多会丢失低序位。 否则，将保留值（带符号或无符号）。 将整型的值转换为浮点值且该值位于可表示的范围外时，结果是不确定的。 （有关整型类型和浮点型的范围的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)。）

下表汇总了来自无符号整型的转换。

## <a name="conversions-from-unsigned-integral-types"></a>从无符号整型的转换

|From|到|方法|
|----------|--------|------------|
|**unsigned char**|**char**|保留位模式；高序位将成为符号位|
|**unsigned char**|**short**|零扩展|
|**unsigned char**|**long**|零扩展|
|**unsigned char**|**unsigned short**|零扩展|
|**unsigned char**|**unsigned long**|零扩展|
|**unsigned char**|**float**|转换为 long；将 long 转换为 float|
|**unsigned char**|**double**|转换为 long；将 long 转换为 double|
|**unsigned char**|**long double**|转换为 long；将 long 转换为 double|
|**unsigned short**|**char**|保留低位字节|
|**unsigned short**|**short**|保留位模式；高序位将成为符号位|
|**unsigned short**|**long**|零扩展|
|**unsigned short**|**unsigned char**|保留低位字节|
|**unsigned short**|**unsigned long**|零扩展|
|**unsigned short**|**float**|转换为 long；将 long 转换为 float|
|**unsigned short**|**double**|转换为 long；将 long 转换为 double|
|**unsigned short**|**long double**|转换为 long；将 long 转换为 double|
|**unsigned long**|**char**|保留低位字节|
|**unsigned long**|**short**|保留低位字|
|**unsigned long**|**long**|保留位模式；高序位将成为符号位|
|**unsigned long**|**unsigned char**|保留低位字节|
|**unsigned long**|**unsigned short**|保留低位字|
|**unsigned long**|**float**|转换为 long；将 long 转换为 float|
|**unsigned long**|**double**|直接转换为 double|
|**unsigned long**|**long double**|转换为 long；将 long 转换为 double|

**Microsoft 专用**

对于 Microsoft C 编译器，unsigned int 类型等效于 unsigned long 类型。 unsigned int 值的转换与 unsigned long 的转换的方式相同。 如果要转换的值大于带正号的最大 **long** 值，则从 **unsigned long** 值到 **float** 的转换不准确。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)  
