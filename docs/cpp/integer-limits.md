---
title: "整数限制 |Microsoft 文档"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5fc79f225d340777751ca513c0fb47dd33e17ad
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2018
---
# <a name="integer-limits"></a>整数限制

**Microsoft 专用**

下表列出了整数类型的限制。 在标准标头文件 <.h > 中也定义了这些限制。

## <a name="limits-on-integer-constants"></a>对整数常量的限制

|返回的常量|含义|“值”|
|--------------|-------------|-----------|
|**CHAR_BIT**|不是位域的最小变量中的位数。|8|
|**SCHAR_MIN**|**signed char** 类型的变量的最小值。|-128|
|**SCHAR_MAX**|**signed char** 类型的变量的最大值。|127|
|**UCHAR_MAX**|最大值类型的变量的**无符号 char**。|255 (0xff)|
|**CHAR_MIN**|最小值的变量的类型**char**。|-128；如果使用了 /J 选项，则为 0|
|**CHAR_MAX**|最大值类型的变量的**char**。|127；如果使用了 /J 选项，则为 255|
|**MB_LEN_MAX**|多字符常量中的最大字节数。|5|
|**SHRT_MIN**|**short** 类型的变量的最小值。|-32768|
|**SHRT_MAX**|**short** 类型的变量的最大值。|32767|
|**USHRT_MAX**|**unsigned short** 类型的变量的最大值。|65535 (0xffff)|
|**INT_MIN**|最小值的变量的类型**int**。|-2147483648|
|**INT_MAX**|最大值类型的变量的**int**。|2147483647|
|**UINT_MAX**|最大值类型的变量的**无符号的整数**。|4294967295 (0xffffffff)|
|**LONG_MIN**|**long** 类型的变量的最小值。|-2147483648|
|**LONG_MAX**|**long** 类型的变量的最大值。|2147483647|
|**ULONG_MAX**|最大值类型的变量的**无符号长**。|4294967295 (0xffffffff)|
|**LLONG_MIN**|最小值的变量的类型**长时间长**|-9223372036854775808|
|**LLONG_MAX**|最大值类型的变量的**长时间长**|9223372036854775807|
|**ULLONG_MAX**|最大值类型的变量的**无符号长时间长**|18446744073709551615 (0xffffffffffffffff)|

如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[浮点限制](../cpp/floating-limits.md)  
