---
title: 浮点限制 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bba2bef20cbe5820d2a7feaae5743f151aea9da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="floating-limits"></a>浮点限制
**Microsoft 专用**  
  
 下表列出了浮点常数的值的限制。 标准头文件中也定义了这些限制\<.h >。  
  
### <a name="limits-on-floating-point-constants"></a>对浮点常量的限制  
  
|返回的常量|含义|值|  
|--------------|-------------|-----------|  
|FLT_DIG DBL_DIG LDBL_DIG|位数 q，以便 q 十进制数的浮点数可以被舍入到浮点表示形式并返回，而不会丢失精度。|6 15 15|  
|FLT_EPSILON DBL_EPSILON LDBL_EPSILON|最小正数 x，以便 x + 1.0 不等于 1.0。|1.192092896e-07F 2.2204460492503131e-016 2.2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG DBL_MANT_DIG LDBL_MANT_DIG|由浮点有效位数中的 FLT_RADIX 指定的基数中的位数。 基数为 2;因此，这些值指定位。|24 53 53|  
|FLT_MAX DBL_MAX LDBL_MAX|最大可表示的浮点数。|3.402823466e+38F 1.7976931348623158e+308 1.7976931348623158e+308|  
|FLT_MAX_10_EXP DBL_MAX_10_EXP LDBL_MAX_10_EXP|最大整数，以便 10 的该数字引发是一个可表示的浮点数。|38 308 308|  
|FLT_MAX_EXP DBL_MAX_EXP LDBL_MAX_EXP|最大整数，以便 FLT_RADIX 的该数字的幂是一个可表示的浮点数。|128 1024 1024|  
|FLT_MIN DBL_MIN LDBL_MIN|最小正值。|1.175494351e-38F 2.2250738585072014e-308 2.2250738585072014e-308|  
|FLT_MIN_10_EXP DBL_MIN_10_EXP LDBL_MIN_10_EXP|最小负整数，以便 10 的该数字引发是可表示的浮点数。|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP DBL_MIN_EXP LDBL_MIN_EXP|最小负整数，以便 FLT_RADIX 的该数字的幂是一个可表示的浮点数。|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX _DBL_RADIX _LDBL_RADIX|基数的指数表示形式。|2 2 2|  
|FLT_ROUNDS _DBL_ROUNDS _LDBL_ROUNDS|浮点加法的舍入模式。|1 (near) 1 (near) 1 (near)|  
  
> [!NOTE]
>  表中信息可能与该产品的将来版本不同。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [整数限制](../cpp/integer-limits.md)