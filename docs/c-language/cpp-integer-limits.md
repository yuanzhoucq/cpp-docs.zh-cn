---
title: C 和C++整数限制
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 6940f36e37ec58ca8fe23c9062928cbf90b125bd
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778377"
---
# <a name="c-and-c-integer-limits"></a>C 和C++整数限制

**Microsoft 专用**

下表列出了 C 和C++中的整数类型限制。 这些限制是在 C 标准标头文件 `<limits.h>` 中定义的。 C++标准库标头 `<limits>` 包括 `<climits>`，其中包含 `<limits.h>`。

Microsoft C 还允许声明大小可变的整数变量，即大小为8、16、32或64位的整数类型。 有关 C 中的大小整数的详细信息，请参阅[调整大小的整数类型](../c-language/c-sized-integer-types.md)。

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
|**LLONG_MIN**|**Long**类型的变量的最小值。|-9223372036854775807-1|
|**LLONG_MAX**|**Long**类型的变量的最大值。|9,223,372,036,854,775,807|
|**ULLONG_MAX**|**无符号 long**类型的变量的最大值。|18446744073709551615（0xffffffffffffffff）|

如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 整数常量](../c-language/c-integer-constants.md)
