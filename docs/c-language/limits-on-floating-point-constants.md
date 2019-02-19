---
title: 对浮点常量的限制
ms.date: 11/04/2016
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
ms.openlocfilehash: df39ee719a4474f6dfd55d31a2848169a1168390
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148746"
---
# <a name="limits-on-floating-point-constants"></a>对浮点常量的限制

**Microsoft 专用**

下表中提供了对浮点常量值的限制。 头文件 FLOAT.H 包含此信息。

### <a name="limits-on-floating-point-constants"></a>对浮点常量的限制

|返回的常量|含义|值|
|--------------|-------------|-----------|
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|位数 q，以便 q 十进制数的浮点数可以被舍入到浮点表示形式并返回，而不会丢失精度。|6<br />15<br />15|
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|最小正数 x，以便 x + 1.0 不等于 1.0|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|
|**FLT_GUARD**||0|
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|由浮点有效位数中的 **FLT_RADIX** 指定的基数中的位数。 基数为 2；因此这些值指定位。|24<br />53<br />53|
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|可表示的最大浮点数。|3.402823466e+38F<br />1.7976931348623158e+308<br />1.7976931348623158e+308|
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|最大整数，以便 10 的该数字的幂是一个可表示的浮点数。|38<br />308<br />308|
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|最大整数，以便 **FLT_RADIX** 的该数字的幂是一个可表示的浮点数。|128<br />1024<br />1024|
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|最小正值。|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|最小负整数，以便 10 的该数字的幂是一个可表示的浮点数。|-37<br />-307<br />-307|
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|最小负整数，以便 **FLT_RADIX** 的该数字的幂是一个可表示的浮点数。|-125<br />-1021<br />-1021|
|**FLT_NORMALIZE**||0|
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|基数的指数表示形式。|2<br />2<br />2|
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|浮点加法的舍入模式。|1（相邻）<br />1（相邻）<br />1（相邻）|

请注意，上表中的信息可能在未来的实现中不同。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 浮点常量](../c-language/c-floating-point-constants.md)
