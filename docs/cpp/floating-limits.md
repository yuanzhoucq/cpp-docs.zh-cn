---
title: 浮点限制
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: cead21c9a66dbc54b46b1c9f8083022a59e80295
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154395"
---
# <a name="floating-limits"></a>浮点限制

**Microsoft 专用**

下表列出了浮点常数的值的限制。 标准标头文件中也定义了这些限制\<float.h >。

## <a name="limits-on-floating-point-constants"></a>对浮点常量的限制

|返回的常量|含义|“值”|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|位数 q，以便 q 十进制数的浮点数可以被舍入到浮点表示形式并返回，而不会丢失精度。|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|最小正数 x，以便 x + 1.0 不等于 1.0。|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|通过指定的基数中的数字位数`FLT_RADIX`在浮点有效位数。 基数为 2;因此这些值指定位。|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|最大可表示的浮点数。|3.402823466e+38F<br/>1.7976931348623158e+308<br/>1.7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|最大整数，以便 10 引发的该数字是一个可表示的浮点数。|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|最大整数，以便`FLT_RADIX`数一个可表示的浮点数字的幂。|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|最小正值。|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|最小负整数，以便 10 引发的该数字是可表示的浮点数。|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|最小负整数，以便`FLT_RADIX`幂数是一个可表示的浮点数。|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|基数的指数表示形式。|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|浮点加法的舍入模式。|1（相邻）<br/>1（相邻）<br/>1（相邻）|

> [!NOTE]
>  表中信息可能与该产品的将来版本不同。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[整数限制](../cpp/integer-limits.md)
