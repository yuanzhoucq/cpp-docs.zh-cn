---
title: C++ 整数限制 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c95e0affa9047aa41ee5ff04b011ac0fbd8d63d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="c-integer-limits"></a>C++ 整数限制

**Microsoft 专用**

下表列出了整数类型的限制。 这些限制在标准标头文件 LIMITS.H 中定义。 Microsoft C 还允许声明固定大小的整数变量，即大小为 8 位、16 位、或 32 位的整数类型。 有关固定大小整数的详细信息，请参阅[固定大小整数类型](../c-language/c-sized-integer-types.md)。

## <a name="limits-on-integer-constants"></a>对整数常量的限制

|**常量**|含义|“值”|
|------------------|-------------|-----------|
|**CHAR_BIT**|不是位域的最小变量中的位数。|8|
|**SCHAR_MIN**|**signed char** 类型的变量的最小值。|-128|
|**SCHAR_MAX**|**signed char** 类型的变量的最大值。|127|
|**UCHAR_MAX**|unsigned char 类型的变量的最大值。|255 (0xff)|
|**CHAR_MIN**|char 类型的变量的最小值。|-128；如果使用了 /J 选项，则为 0|
|**CHAR_MAX**|char 类型的变量的最大值。|127；如果使用了 /J 选项，则为 255|
|**MB_LEN_MAX**|多字符常量中的最大字节数。|5|
|**SHRT_MIN**|**short** 类型的变量的最小值。|-32768|
|**SHRT_MAX**|**short** 类型的变量的最大值。|32767|
|**USHRT_MAX**|**unsigned short** 类型的变量的最大值。|65535 (0xffff)|
|**INT_MIN**|int 类型的变量的最小值。|-2147483647 - 1|
|**INT_MAX**|int 类型的变量的最大值。|2147483647|
|**UINT_MAX**|unsigned int 类型的变量的最大值。|4294967295 (0xffffffff)|
|**LONG_MIN**|**long** 类型的变量的最小值。|-2147483647 - 1|
|**LONG_MAX**|**long** 类型的变量的最大值。|2147483647|
|**ULONG_MAX**|unsigned long 类型的变量的最大值。|4294967295 (0xffffffff)|

如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 整数常量](../c-language/c-integer-constants.md)  
