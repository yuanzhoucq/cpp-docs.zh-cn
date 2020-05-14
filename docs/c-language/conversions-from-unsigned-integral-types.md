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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998787"
---
# <a name="conversions-from-unsigned-integral-types"></a>从无符号整型的转换

当无符号整数转换为整数或浮点类型时，如果原始值可以在结果类型中表示，则该值不变。

将无符号整数转换为更大的整数时，该值扩展为零。 当转换成较小的整数时，高序位将被截断。 使用结果类型解释结果，如本例所示。

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

将无符号整数转换为浮点类型时，如果原始值不能在结果类型中完全表示，则结果是下一个更高或更低的可表示值。

有关整型和浮点类型大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)。

**Microsoft 专用**

在 Microsoft 编译器中，unsigned（或 unsigned int）和 unsigned long 是不同但等效的类型    。 unsigned int 值的转换与 unsigned long 的转换的方式相同   。

**结束 Microsoft 专用**

下表汇总了来自无符号整型的转换。

## <a name="table-of-conversions-from-unsigned-integral-types"></a>从无符号整型转换的表

|From|功能|方法|
|----------|--------|------------|
|**unsigned char**|**char**|保留位模式；高序位将成为符号位|
|**unsigned char**|**short**|零扩展|
|**unsigned char**|**long**|零扩展|
|**unsigned char**|**long long**|零扩展|
|**unsigned char**|**unsigned short**|零扩展|
|**unsigned char**|**unsigned long**|零扩展|
|**unsigned char**|**unsigned long long**|零扩展|
|**unsigned char**|**float**|转换为 long  ；将 long  转换为  float|
|**unsigned char**|**double**|转换为 long  ；将 long  转换为  double|
|**unsigned char**|**long double**|转换为 long  ；将 long  转换为  double|
|**unsigned short**|**char**|保留低位字节|
|**unsigned short**|**short**|保留位模式；高序位将成为符号位|
|**unsigned short**|**long**|零扩展|
|**unsigned short**|**long long**|零扩展|
|**unsigned short**|**unsigned char**|保留低位字节|
|**unsigned short**|**unsigned long**|零扩展|
|**unsigned short**|**unsigned long long**|零扩展|
|**unsigned short**|**float**|转换为 long  ；将 long  转换为  float|
|**unsigned short**|**double**|转换为 long  ；将 long  转换为  double|
|**unsigned short**|**long double**|转换为 long  ；将 long  转换为  double|
|**unsigned long**|**char**|保留低位字节|
|**unsigned long**|**short**|保留低位字|
|**unsigned long**|**long**|保留位模式；高序位将成为符号位|
|**unsigned long**|**long long**|零扩展|
|**unsigned long**|**unsigned char**|保留低位字节|
|**unsigned long**|**unsigned short**|保留低位字|
|**unsigned long**|**unsigned long long**|零扩展|
|**unsigned long**|**float**|转换为 long  ；将 long  转换为  float|
|**unsigned long**|**double**|直接转换为 double |
|**unsigned long**|**long double**|转换为 long  ；将 long  转换为  double|
|**unsigned long long**|**char**|保留低位字节|
|**unsigned long long**|**short**|保留低位字|
|**unsigned long long**|**long**|保留低位双字节|
|**unsigned long long**|**long long**|保留位模式；高序位将成为符号位|
|**unsigned long long**|**unsigned char**|保留低位字节|
|**unsigned long long**|**unsigned short**|保留低位字|
|**unsigned long long**|**unsigned long**|保留低位双字节|
|**unsigned long long**|**float**|转换为 long  ；将 long  转换为  float|
|**unsigned long long**|**double**|直接转换为 double |
|**unsigned long long**|**long double**|转换为 long  ；将 long  转换为  double|

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
