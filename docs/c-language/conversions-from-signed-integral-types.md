---
title: 从带符号整型的转换
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998720"
---
# <a name="conversions-from-signed-integral-types"></a>从带符号整型的转换

当有符号整数转换为整数或浮点类型时，如果原始值可以在结果类型中表示，则该值不变。

当有符号整数转换为更大的整数时，该值将被符号扩展。 当转换成较小的整数时，高序位将被截断。 使用结果类型解释结果，如本例所示：

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

将带符号整数转换为浮点类型时，如果原始值不能在结果类型中完全表示，则结果是下一个更高或更低的可表示值。

有关整型和浮点类型大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)。

下表汇总了来自带符号整型的转换。 它假定默认情况下，“char”类型是带符号的  。 如果使用编译时选项将 char 类型的默认值更改为无符号，则应用 unsigned char 类型的[从无符号整型转换](../c-language/conversions-from-unsigned-integral-types.md)表中给定的转换，而不是应用此表中的转换   。

**Microsoft 专用**

在 Microsoft 编译器中，int 和 long 是不同但等效的类型   。 int 值的转换与 long 的转换的方式相同   。

**结束 Microsoft 专用**

## <a name="table-of-conversions-from-signed-integral-types"></a>从带符号整型转换的表

|From|功能|方法|
|----------|--------|------------|
|**char**<sup>1</sup>|**short**|符号扩展|
|**char**|**long**|符号扩展|
|**char**|**long long**|符号扩展|
|**char**|**unsigned char**|保留模式；高序位失去符号位的函数|
|**char**|**unsigned short**|符号扩展至 **short**；将 **short** 转换为 **unsigned short**|
|**char**|**unsigned long**|符号扩展至 **long**；将 **long** 转换为 **unsigned long**|
|**char**|**unsigned long long**|符号扩展至 long long；将 long long 转换为 unsigned long long   |
|**char**|**float**|符号扩展至 **long**；将 **long** 转换为 **float**|
|**char**|**double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**char**|**long double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**short**|**char**|保留低位字节|
|**short**|**long**|符号扩展|
|**short**|**long long**|符号扩展|
|**short**|**unsigned char**|保留低位字节|
|**short**|**unsigned short**|保留位模式；高序位丢失符号位的函数|
|**short**|**unsigned long**|符号扩展至 **long**；将 **long** 转换为 **unsigned long**|
|**short**|**unsigned long long**|符号扩展至 long long；将 long long 转换为 unsigned long long   |
|**short**|**float**|符号扩展至 **long**；将 **long** 转换为 **float**|
|**short**|**double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**short**|**long double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**long**|**char**|保留低位字节|
|**long**|**short**|保留低位字|
|**long**|**long long**|符号扩展|
|**long**|**unsigned char**|保留低位字节|
|**long**|**unsigned short**|保留低位字|
|**long**|**unsigned long**|保留位模式；高序位丢失符号位的函数|
|**long**|**unsigned long long**|符号扩展至 long long；将 long long 转换为 unsigned long long   |
|**long**|**float**|表示为 **float**。 如果不能精确表示 long，则某些精度将丢失  。|
|**long**|**double**|表示为 **double**。 如果 long 不能精确表示为 double，则某些精度将丢失   。|
|**long**|**long double**|表示为 **double**。 如果 long 不能精确表示为 double，则某些精度将丢失   。|
|**long long**|**char**|保留低位字节|
|**long long**|**short**|保留低位字|
|**long long**|**long**|保留低位双字节|
|**long long**|**unsigned char**|保留低位字节|
|**long long**|**unsigned short**|保留低位字|
|**long long**|**unsigned long**|保留低位双字节|
|**long long**|**unsigned long long**|保留位模式；高序位丢失符号位的函数|
|**long long**|**float**|表示为 **float**。 如果不能精确表示 long long，则某些精度将丢失  。|
|**long long**|**double**|表示为 **double**。 如果 long long 不能精确表示为 double，则某些精度将丢失   。|
|**long long**|**long double**|表示为 **double**。 如果 long long 不能精确表示为 double，则某些精度将丢失   。|

<sup>1</sup> 所有 char 项假定默认情况下 char 类型是有符号的   。

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
