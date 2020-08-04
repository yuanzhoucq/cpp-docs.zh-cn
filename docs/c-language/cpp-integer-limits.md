---
title: C 和 C++ 整数限制
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 1484b43719696578be437909351e24a550ec9869
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217111"
---
# <a name="c-and-c-integer-limits"></a>C 和 C++ 整数限制

**Microsoft 专用**

下表列出了 C 和 C++ 整数类型的限制。 这些限制在 C 标准标头文件 `<limits.h>` 中定义。 C++ 标准库标头 `<limits>` 包括 `<climits>`，其中包括 `<limits.h>`。

Microsoft C 还允许声明固定大小的整数变量，即大小为 8 位、16 位、32 位或 64 位的整数类型。 有关 C 中固定大小整数的详细信息，请参阅[固定大小整数类型](../c-language/c-sized-integer-types.md)。

## <a name="limits-on-integer-constants"></a>对整数常量的限制

|**常量**|含义|“值”|
|------------------|-------------|-----------|
|**CHAR_BIT**|不是位域的最小变量中的位数。|8|
|**SCHAR_MIN**|类型为 `signed char` 的变量的最小值。|-128|
|**SCHAR_MAX**|类型为 `signed char` 的变量的最大值。|127|
|**UCHAR_MAX**|类型为 `unsigned char` 的变量的最大值。|255 (0xff)|
|**CHAR_MIN**|类型为 `char` 的变量的最小值。|-128；如果使用了 /J 选项，则为 0|
|**CHAR_MAX**|类型为 `char` 的变量的最大值。|127；如果使用了 /J 选项，则为 255|
|**MB_LEN_MAX**|多字符常量中的最大字节数。|5|
|**SHRT_MIN**|类型为 `short` 的变量的最小值。|-32768|
|**SHRT_MAX**|类型为 `short` 的变量的最大值。|32767|
|**USHRT_MAX**|类型为 `unsigned short` 的变量的最大值。|65535 (0xffff)|
|**INT_MIN**|类型为 `int` 的变量的最小值。|-2147483647 - 1|
|**INT_MAX**|类型为 `int` 的变量的最大值。|2147483647|
|**UINT_MAX**|类型为 `unsigned int` 的变量的最大值。|4294967295 (0xffffffff)|
|**LONG_MIN**|类型为 `long` 的变量的最小值。|-2147483647 - 1|
|**LONG_MAX**|类型为 `long` 的变量的最大值。|2147483647|
|**ULONG_MAX**|类型为 `unsigned long` 的变量的最大值。|4294967295 (0xffffffff)|
|**LLONG_MIN**|类型为 `long long` 的变量的最小值。|-9,223,372,036,854,775,807 - 1|
|**LLONG_MAX**|类型为 `long long` 的变量的最大值。|9,223,372,036,854,775,807|
|**ULLONG_MAX**|类型为 `unsigned long long` 的变量的最大值。|18,446,744,073,709,551,615 (0xffffffffffffffff)|

如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 整数常量](../c-language/c-integer-constants.md)
