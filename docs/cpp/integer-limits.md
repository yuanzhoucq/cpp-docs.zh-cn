---
title: 整数限制
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: a113dd687e6f135af950f461e024b9fd9feaf1b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213380"
---
# <a name="integer-limits"></a>整数限制

**Microsoft 专用**

下表列出了整数类型的限制。 当包含标准头文件时，也会定义这些限制的预处理器宏 \<climits> 。

## <a name="limits-on-integer-constants"></a>对整数常量的限制

| 返回的常量 | 含义 | “值” |
|--|--|--|
| `CHAR_BIT` | 不是位域的最小变量中的位数。 | 8 |
| `SCHAR_MIN` | 类型的变量的最小值 **`signed char`** 。 | -128 |
| `SCHAR_MAX` | 类型的变量的最大值 **`signed char`** 。 | 127 |
| `UCHAR_MAX` | 类型的变量的最大值 **`unsigned char`** 。 | 255 (0xff) |
| `CHAR_MIN` | 类型的变量的最小值 **`char`** 。 | -128;如果使用了选项，则为 0 **`/J`** |
| `CHAR_MAX` | 类型的变量的最大值 **`char`** 。 | 127;如果使用了选项，则为 255 **`/J`** |
| `MB_LEN_MAX` | 多字符常量中的最大字节数。 | 5 |
| `SHRT_MIN` | 类型的变量的最小值 **`short`** 。 | -32768 |
| `SHRT_MAX` | 类型的变量的最大值 **`short`** 。 | 32767 |
| `USHRT_MAX` | 类型的变量的最大值 **`unsigned short`** 。 | 65535 (0xffff) |
| `INT_MIN` | 类型的变量的最小值 **`int`** 。 | -2147483648 |
| `INT_MAX` | 类型的变量的最大值 **`int`** 。 | 2147483647 |
| `UINT_MAX` | 类型的变量的最大值 **`unsigned int`** 。 | 4294967295 (0xffffffff) |
| `LONG_MIN` | 类型的变量的最小值 **`long`** 。 | -2147483648 |
| `LONG_MAX` | 类型的变量的最大值 **`long`** 。 | 2147483647 |
| `ULONG_MAX` | 类型的变量的最大值 **`unsigned long`** 。 | 4294967295 (0xffffffff) |
| `LLONG_MIN` | 类型的变量的最小值**`long long`** | -9223372036854775808 |
| `LLONG_MAX` | 类型的变量的最大值**`long long`** | 9223372036854775807 |
| `ULLONG_MAX` | 类型的变量的最大值**`unsigned long long`** | 18446744073709551615 (0xffffffffffffffff) |

如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。

## <a name="see-also"></a>另请参阅

[浮动限制](../cpp/floating-limits.md)
