---
title: 整数限制
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: 75cd05e73aba2d2e82e8077e0a289d8b0fae7ec4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178219"
---
# <a name="integer-limits"></a>整数限制

**Microsoft 专用**

下表列出了整数类型的限制。 这些限制也在标准标头文件中定义，\<限制 .h >。

## <a name="limits-on-integer-constants"></a>对整数常量的限制

|一直|含义|值|
|--------------|-------------|-----------|
|CHAR_BIT|不是位域的最小变量中的位数。|8|
|SCHAR_MIN|**signed char** 类型的变量的最小值。|-128|
|SCHAR_MAX|**signed char** 类型的变量的最大值。|127|
|UCHAR_MAX|unsigned char 类型的变量的最大值。|255 (0xff)|
|CHAR_MIN|char 类型的变量的最小值。|-128；如果使用了 /J 选项，则为 0|
|CHAR_MAX|char 类型的变量的最大值。|127；如果使用了 /J 选项，则为 255|
|MB_LEN_MAX|多字符常量中的最大字节数。|5|
|SHRT_MIN|**short** 类型的变量的最小值。|-32768|
|SHRT_MAX|**short** 类型的变量的最大值。|32767|
|USHRT_MAX|**unsigned short** 类型的变量的最大值。|65535 (0xffff)|
|INT_MIN|int 类型的变量的最小值。|-2147483648|
|INT_MAX|int 类型的变量的最大值。|2147483647|
|UINT_MAX|unsigned int 类型的变量的最大值。|4294967295 (0xffffffff)|
|LONG_MIN|**long** 类型的变量的最小值。|-2147483648|
|LONG_MAX|**long** 类型的变量的最大值。|2147483647|
|ULONG_MAX|unsigned long 类型的变量的最大值。|4294967295 (0xffffffff)|
|LLONG_MIN|**Long**类型的变量的最小值|-9223372036854775808|
|LLONG_MAX|**Long**类型的变量的最大值|9223372036854775807|
|ULLONG_MAX|**无符号 long**类型的变量的最大值|18446744073709551615 (0xffffffffffffffff)|

如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[浮点限制](../cpp/floating-limits.md)
