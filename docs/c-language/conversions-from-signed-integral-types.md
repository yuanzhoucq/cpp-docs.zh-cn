---
title: 从带符号整型的转换
ms.date: 11/04/2016
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 4d2f0ab43adf3cbad3d1ffa244551c67883c6606
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152776"
---
# <a name="conversions-from-signed-integral-types"></a>从带符号整型的转换

当一个带符号整数转换为一个具有相等或更大大小的无符号整数且该带符号整数的值不为负时，值保持不变。 转换是通过对带符号整数进行符号扩展来实现的。 通过截断高位将带符号整数转换为较短的带符号整数。 结果被解释为无符号值，如此示例中所示。

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

将带符号整数转换为浮点值时，不会丢任何信息，只不过在将 **long int** 或 **unsigned long int** 值转换为 **float** 值时，可能会丢失某些精度。

下表汇总了来自带符号整型的转换。 此表假定默认情况下 **char** 类型是带符号的。 如果使用编译时选项将 **char** 类型的默认值更改为无符号，则应用 **unsigned char** 类型的[从无符号整型转换](../c-language/conversions-from-unsigned-integral-types.md)表中给定的转换，而不是应用“从带符号整型转换”表中给定的转换。

### <a name="conversions-from-signed-integral-types"></a>从带符号整型的转换

|From|到|方法|
|----------|--------|------------|
|**char**1|**short**|符号扩展|
|**char**|**long**|符号扩展|
|**char**|**unsigned char**|保留模式；高序位失去符号位的函数|
|**char**|**unsigned short**|符号扩展至 **short**；将 **short** 转换为 **unsigned short**|
|**char**|**unsigned long**|符号扩展至 **long**；将 **long** 转换为 **unsigned long**|
|**char**|**float**|符号扩展至 **long**；将 **long** 转换为 **float**|
|**char**|**double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**char**|**long double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**short**|**char**|保留低位字节|
|**short**|**long**|符号扩展|
|**short**|**unsigned char**|保留低位字节|
|**short**|**unsigned short**|保留位模式；高序位丢失符号位的函数|
|**short**|**unsigned long**|符号扩展至 **long**；将 **long** 转换为 **unsigned long**|
|**short**|**float**|符号扩展至 **long**；将 **long** 转换为 **float**|
|**short**|**double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**short**|**long double**|符号扩展至 **long**；将 **long** 转换为 **double**|
|**long**|**char**|保留低位字节|
|**long**|**short**|保留低位字|
|**long**|**unsigned char**|保留低位字节|
|**long**|**unsigned short**|保留低位字|
|**long**|**unsigned long**|保留位模式；高序位丢失符号位的函数|
|**long**|**float**|表示为 **float**。 如果不能精确表示 **long**，则某些精度将丢失。|
|**long**|**double**|表示为 **double**。 如果 **long** 不能精确表示为 **double**，则某些精度将丢失。|
|**long**|**long double**|表示为 **double**。 如果 **long** 不能精确表示为 **double**，则某些精度将丢失。|

1. 所有 **char** 项假定默认情况下 **char** 类型是有符号的。

**Microsoft 专用**

对于 Microsoft 32 位 C 编译器，整数与 **long** 等效。 **int** 值的转换与 **long** 的相同。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
