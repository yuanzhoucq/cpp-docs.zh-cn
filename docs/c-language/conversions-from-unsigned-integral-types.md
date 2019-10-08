---
title: 从无符号整型的转换
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998787"
---
# <a name="conversions-from-unsigned-integral-types"></a>从无符号整型的转换

当无符号整数转换为整数或浮点类型时，如果在结果类型中可表示原始值，则该值不变。

将无符号整数转换为较大大小的整数时，值为零扩展。 转换为较小的整数时，将截断高序位。 将使用结果类型解释结果，如本示例中所示。

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

将无符号整数转换为浮点类型时，如果不能准确地表示结果类型中的原始值，则结果将是下一个更高或较低的可表示值。

请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)以获取有关整型和浮点类型大小的信息。

**Microsoft 专用**

在 Microsoft 编译器中，**无符号**的（无**符号整数**）和**无符号 long**都是不同的，但等效类型。 unsigned int 值的转换与 unsigned long 的转换的方式相同。

**结束 Microsoft 专用**

下表汇总了来自无符号整型的转换。

## <a name="table-of-conversions-from-unsigned-integral-types"></a>来自无符号整型的转换表

|From|功能|方法|
|----------|--------|------------|
|**unsigned char**|**char**|保留位模式；高序位将成为符号位|
|**unsigned char**|**short**|零扩展|
|**unsigned char**|**long**|零扩展|
|**unsigned char**|**long long**|零扩展|
|**unsigned char**|**unsigned short**|零扩展|
|**unsigned char**|**unsigned long**|零扩展|
|**unsigned char**|**无符号长长**|零扩展|
|**unsigned char**|**float**|转换为 long；将 long 转换为float|
|**unsigned char**|**double**|转换为 long；将 long 转换为double|
|**unsigned char**|**long double**|转换为 long；将 long 转换为double|
|**unsigned short**|**char**|保留低位字节|
|**unsigned short**|**short**|保留位模式；高序位将成为符号位|
|**unsigned short**|**long**|零扩展|
|**unsigned short**|**long long**|零扩展|
|**unsigned short**|**unsigned char**|保留低位字节|
|**unsigned short**|**unsigned long**|零扩展|
|**unsigned short**|**无符号长长**|零扩展|
|**unsigned short**|**float**|转换为 long；将 long 转换为float|
|**unsigned short**|**double**|转换为 long；将 long 转换为double|
|**unsigned short**|**long double**|转换为 long；将 long 转换为double|
|**unsigned long**|**char**|保留低位字节|
|**unsigned long**|**short**|保留低位字|
|**unsigned long**|**long**|保留位模式；高序位将成为符号位|
|**unsigned long**|**long long**|零扩展|
|**unsigned long**|**unsigned char**|保留低位字节|
|**unsigned long**|**unsigned short**|保留低位字|
|**unsigned long**|**无符号长长**|零扩展|
|**unsigned long**|**float**|转换为 long；将 long 转换为float|
|**unsigned long**|**double**|直接转换为 double|
|**unsigned long**|**long double**|转换为 long；将 long 转换为double|
|**无符号长长**|**char**|保留低位字节|
|**无符号长长**|**short**|保留低位字|
|**无符号长长**|**long**|保留低序位 dword|
|**无符号长长**|**long long**|保留位模式；高序位将成为符号位|
|**无符号长长**|**unsigned char**|保留低位字节|
|**无符号长长**|**unsigned short**|保留低位字|
|**无符号长长**|**unsigned long**|保留低序位 dword|
|**无符号长长**|**float**|转换为 long；将 long 转换为float|
|**无符号长长**|**double**|直接转换为 double|
|**无符号长长**|**long double**|转换为 long；将 long 转换为double|

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
