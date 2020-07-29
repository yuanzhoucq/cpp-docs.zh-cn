---
title: 数据类型常量
ms.date: 06/25/2018
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
ms.openlocfilehash: d9d053611fb733d55424d01be2bab030fc49e6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215161"
---
# <a name="data-type-constants"></a>数据类型常量

数据类型常量是实现相关的整型和浮点数据类型允许的值范围。

## <a name="integral-type-constants"></a>整型类型常量

这些常量提供了整型数据类型的范围。 要使用这些常量，请在源文件中包含 limits.h 标头：

```C
#include <limits.h>
```

> [!NOTE]
> [`/J`](../build/reference/j-default-char-type-is-unsigned.md)编译器选项将默认 **`char`** 类型从更改 **`signed char`** 为 **`unsigned char`** 。

|返回的常量|值|描述|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|中的位数**`char`**|
|**SCHAR_MIN**|(-128)|最小 **`signed char`** 值|
|**SCHAR_MAX**|127|最大 **`signed char`** 值|
|**UCHAR_MAX**|255 (0xff)|最大 **`unsigned char`** 值|
|**CHAR_MIN**|（-128）（如果使用了选项，则为 0 **`/J`** ）|最小 **`char`** 值|
|**CHAR_MAX**|127（如果使用了选项，则为 255 **`/J`** ）|最大 **`char`** 值|
|**MB_LEN_MAX**|5|多字节中的最大字节数**`char`**|
|**SHRT_MIN**|-32768|最小 **`signed short`** 值|
|**SHRT_MAX**|32767|最大 **`signed short`** 值|
|**USHRT_MAX**|65535 (0xffff)|最大 **`unsigned short`** 值|
|**INT_MIN**|(-2147483647 - 1)|最小 **`signed int`** 值|
|**INT_MAX**|2147483647|最大 **`signed int`** 值|
|**UINT_MAX**|4294967295 (0xffffffff)|最大 **`unsigned int`** 值|
|**LONG_MIN**|(-2147483647L - 1)|最小 **`signed long`** 值|
|**LONG_MAX**|2147483647L|最大 **`signed long`** 值|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|最大 **`unsigned long`** 值|
|**LLONG_MIN**|(-9223372036854775807LL - 1)|最 **`signed long long`** 小 **`__int64`** 值或值|
|**LLONG_MAX**|9223372036854775807LL|最 **`signed long long`** 大 **`__int64`** 值或值|
|**ULLONG_MAX**|0xffffffffffffffffull|最大 **`unsigned long long`** 值|
|**_I8_MIN**|(-127i8 - 1)|最小有符号的 8 位数值|
|**_I8_MAX**|127i8|最大有符号的 8 位数值|
|**_UI8_MAX**|0xffui8|最大无符号的 8 位数值|
|**_I16_MIN**|(-32767i16 - 1)|最小有符号的 16 位数值|
|**_I16_MAX**|32767i16|最大有符号的 16 位数值|
|**_UI16_MAX**|0xffffui16|最大无符号的 16 位数值|
|**_I32_MIN**|(-2147483647i32 - 1)|最小有符号的 32 位数值|
|**_I32_MAX**|2147483647i32|最大有符号的 32 位数值|
|**_UI32_MAX**|0xffffffffui32|最大无符号的 32 位数值|
|**_I64_MIN**|(-9223372036854775807 - 1)|最小有符号的 64 位数值|
|**_I64_MAX**|9223372036854775807|最大有符号的 64 位数值|
|**_UI64_MAX**|0xffffffffffffffffui64|最大无符号的 64 位数值|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128 - 1)|最小有符号的 128 位数值|
|**_I128_MAX**|170141183460469231731687303715884105727i128|最大有符号的 128 位数值|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|最大无符号的 128 位数值|
|**SIZE_MAX**|如果已定义 _WIN64 或为 UINT_MAX，则与 _UI64_MAX 相同************|最大本机整数大小|
|**RSIZE_MAX**|与 (SIZE_MAX >> 1) 相同****|最大安全裤整数大小|

## <a name="floating-point-type-constants"></a>浮点类型常量

以下常量给出了 **`long double`** 、 **`double`** 和数据类型的范围和其他特性 **`float`** 。 要使用这些常量，请在源文件中包含 float.h 标头：

```C
#include <float.h>
```

|返回的常量|值|描述|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|十进制位数的舍入精度|
|**DBL_DIG**|15|精度的小数位数|
|**DBL_EPSILON**|2.2204460492503131e-016|最小，这样 1.0 + DBL_EPSILON != 1.0****|
|**DBL_HAS_SUBNORM**|1|类型支持低能数（非规格化）数|
|**DBL_MANT_DIG**|53|有效数字（尾数）的位数|
|**DBL_MAX**|1.7976931348623158e+308|最大值|
|**DBL_MAX_10_EXP**|308|最大十进制指数|
|**DBL_MAX_EXP**|1024|最大二进制指数|
|**DBL_MIN**|2.2250738585072014e-308|最小正规值|
|**DBL_MIN_10_EXP**|(-307)|最小十进制指数|
|**DBL_MIN_EXP**|(-1021)|最小二进制指数|
|**_DBL_RADIX**|2|指数基数|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|最小次正规值|
|**FLT_DECIMAL_DIG**|9|十进制位数的舍入精度|
|**FLT_DIG**|6|十进制位数的精度|
|**FLT_EPSILON**|1.192092896e-07F|最小，这样 1.0 + FLT_EPSILON != 1.0****|
|**FLT_HAS_SUBNORM**|1|类型支持低能数（非规格化）数|
|**FLT_MANT_DIG**|24|有效数字（尾数）的位数|
|**FLT_MAX**|3.402823466e+38F|最大值|
|**FLT_MAX_10_EXP**|38|最大十进制指数|
|**FLT_MAX_EXP**|128|最大二进制指数|
|**FLT_MIN**|1.175494351e-38F|最小正规值|
|**FLT_MIN_10_EXP**|(-37)|最小十进制指数|
|**FLT_MIN_EXP**|(-125)|最小二进制指数|
|**FLT_RADIX**|2|指数基数|
|**FLT_TRUE_MIN**|1.401298464e-45F|最小次正规值|
|**LDBL_DIG**|15|精度的小数位数|
|**LDBL_EPSILON**|2.2204460492503131e-016|最小，这样 1.0 + LDBL_EPSILON != 1.0****|
|**LDBL_HAS_SUBNORM**|1|类型支持低能数（非规格化）数|
|**LDBL_MANT_DIG**|53|有效数字（尾数）的位数|
|**LDBL_MAX**|1.7976931348623158e+308|最大值|
|**LDBL_MAX_10_EXP**|308|最大十进制指数|
|**LDBL_MAX_EXP**|1024|最大二进制指数|
|**LDBL_MIN**|2.2250738585072014e-308|最小正规值|
|**LDBL_MIN_10_EXP**|(-307)|最小十进制指数|
|**LDBL_MIN_EXP**|(-1021)|最小二进制指数|
|**_LDBL_RADIX**|2|指数基数|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|最小次正规值|
|**DECIMAL_DIG**|与 DBL_DECIMAL_DIG 相同****|默认（双精度）十进制位数的舍入精度|

## <a name="see-also"></a>另请参阅

[全局常量](../c-runtime-library/global-constants.md)
