---
title: _itoa，_itow功能
ms.date: 4/2/2020
api_name:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: 0cc084076c5e39843ecc1afa08671ce6b2f06d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342701"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa、_itoa、ltoa、_ltoa、ultoa、_ultoa、_i64toa、_ui64toa、_itow、_ltow、_ultow、_i64tow、_ui64tow

将整数转换为字符串。 这些函数的更安全的版本可用;请参阅[_itoa_s、_itow_s函数](itoa-s-itow-s.md)。

## <a name="syntax"></a>语法

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These POSIX versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>参数

*value*<br/>
要转换的数字。

*缓冲区*<br/>
保存转换结果的缓冲区。

*拉迪克斯*<br/>
用于转换*值*的基数，必须在 2-36 范围内。

*大小*<br/>
缓冲区的长度（以字符类型的单位为单位）。 此参数从C++中的*缓冲区*参数推断。

## <a name="return-value"></a>返回值

每个函数都返回一个指向*缓冲区的指针*。 无错误返回。

## <a name="remarks"></a>备注

**_itoa**_itoa、_ltoa、_ultoa、_i64toa **_i64toa**和 **_ui64toa**函数将给定*值*参数的数字转换为 null 端接字符串，并将结果 **_ltoa****（_itoa、_ltoa**和 **_ultoa**最多 33 个字符）和缓冲区 **_ltoa***中***65 个字符_i64toa**和 **_ultoa****_ui64toa）。** 如果*半径*等于 10，*并且值*为负数，则存储字符串的第一个字符是负号 （）。**-** **_itow**_itow、_ltow、_ultow、_i64tow **_i64tow**和 **_ui64tow**函数分别为 **_ltow****_ultow****_itoa****_itoa、_ltoa、_ultoa、_i64toa**和 **_ui64toa**的宽 **_ultoa**字符版本 **_i64toa**。

> [!IMPORTANT]
> 这些函数可以写入缓冲区的末尾太小。 为了防止缓冲区溢出，请确保*缓冲区*足够大，可以容纳转换的数字加上尾随的空字符和符号字符。 滥用这些功能可能会导致代码出现严重的安全问题。

由于其潜在的安全问题，默认情况下，这些函数会导致弃用警告[C4996：](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)**此函数或变量可能不安全。请考虑改用***safe_function。* **要禁用弃用，请使用_CRT_SECURE_NO_WARNINGS。** 我们建议您更改源代码以使用警告消息建议的*safe_function。* 更安全的函数不会写入比指定的缓冲区大小更多的字符。 有关详细信息，请参阅[_itoa_s，_itow_s函数](itoa-s-itow-s.md)。

要在不使用弃用警告的情况下使用这些函数，请先定义 **_CRT_SECURE_NO_WARNINGS**预处理器宏，然后再包括任何 CRT 标头。 通过将 **/D_CRT_SECURE_NO_WARNINGS**编译器选项添加到**cl**命令，可以在开发人员命令提示符中的命令行上执行此操作。 否则，在源文件中定义宏。 如果使用预编译标头，请在预编译标头顶部定义宏，包括文件*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）。* 要在源代码中定义宏，请在包含任何 CRT 标头之前使用 **#define**指令，如以下示例所示：

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

在C++，这些函数具有模板重载，用于调用其更安全的对应函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

POSIX 名称**itoa、ltoa**和**ultoa** **ltoa**作为 **_itoa、_ltoa**和 **_ltoa****_ultoa**函数的别名存在。 POSIX 名称被弃用，因为它们不遵循 ISO C 特定于实现的全局函数名称约定。默认情况下，这些函数会导致弃用警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)：**此项目的 POSIX 名称被弃用。相反，请使用 ISO C 和C++符合性名称：new_name** *new_name*。 我们建议您更改源代码以使用这些函数的更安全版本 **，_itoa_s、_ltoa_s**或 **_ultoa_s。** **_ltoa_s** 有关详细信息，请参阅[_itoa_s，_itow_s函数](itoa-s-itow-s.md)。

对于源代码可移植性，您可能更喜欢在代码中保留 POSIX 名称。 要在不使用弃用警告的情况下使用这些函数，请先定义 **_CRT_NONSTDC_NO_WARNINGS**和 **_CRT_SECURE_NO_WARNINGS**预处理器宏，然后再包括任何 CRT 标头。 通过将 **/D_CRT_SECURE_NO_WARNINGS**和 **/D_CRT_NONSTDC_NO_WARNINGS**编译器选项添加到**cl**命令，可以在开发人员命令提示符中的命令行上执行此操作。 否则，请定义源文件中的宏。 如果使用预编译标头，请定义预编译标头顶部的宏包括文件。 要在源代码中定义宏，请在包含任何 CRT 标头之前使用 **#define**指令，如以下示例所示：

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大转化计数宏

为了帮助您为转换创建安全缓冲区，CRT 包含一些方便的宏。 这些定义转换多个常见基的每个整数类型（包括空终止符和符号字符）的最长可能值所需的缓冲区大小。 为了确保转换缓冲区足够大，足以接收*radix*指定的基中的任何转换，在分配缓冲区时使用这些定义的宏之一。 这有助于防止将积分类型转换为字符串时缓冲区溢出错误。 当您在源中包括 stdlib.h 或 wchar.h 时，将定义这些宏。

要在字符串转换函数中使用这些宏之一，请声明相应字符类型的转换缓冲区，并将整数类型和基的宏值用作缓冲区维度。 下表列出了适用于列出的基础的每个函数的宏：

||||
|-|-|-|
|函数|radix|宏|
|**_itoa**， **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**， **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**， **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**， **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**， **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

此示例使用转换计数宏定义足够大的缓冲区，以包含基 2 中**长的未签名长**缓冲区：

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**伊托亚**，**伊托亚**，**乌尔托亚**|\<stdlib.h>|
|**_itoa**， **_ltoa**， **_ultoa**， **_i64toa**， **_ui64toa**|\<stdlib.h>|
|**_itow，** **_ltow**， **_ultow**， **_i64tow**， **_ui64tow**|\<stdlib.h> 或 \<wchar.h>|

这些函数和宏特定于 Microsoft。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此示例演示了某些整数转换函数的使用。 请注意使用 **_CRT_SECURE_NO_WARNINGS**宏来静默警告 C4996。

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s，_itow_s功能](itoa-s-itow-s.md)<br/>
