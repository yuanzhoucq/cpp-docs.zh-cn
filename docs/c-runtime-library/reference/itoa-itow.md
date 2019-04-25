---
title: _itoa，_itow 函数
ms.date: 03/21/2018
apiname:
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
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 016f3474345b623415be9fe33556bb9f466542ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157365"
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa、 _itoa、 ltoa、 _ltoa、 ultoa、 _ultoa、 _i64toa、 _ui64toa、 _itow、 _ltow、 _ultow、 _i64tow、 _ui64tow

将整数转换为字符串。 这些函数的更多安全版本才会有效。请参阅[_itoa_s、 _itow_s 函数](itoa-s-itow-s.md)。

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

// These Posix versions of the functions have deprecated names:
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

*值*<br/>
要转换的数字。

*buffer*<br/>
包含转换的结果的缓冲区。

*radix*<br/>
若要使用的转换的基*值*，它必须是 2 36 的范围中。

*size*<br/>
中的字符类型的单位的缓冲区的长度。 此参数来推断*缓冲区*中的参数C++。

## <a name="return-value"></a>返回值

这些函数均返回一个指向*缓冲区*。 无错误返回。

## <a name="remarks"></a>备注

**_Itoa**， **_ltoa**， **_ultoa**， **_i64toa**，并 **_ui64toa**函数将转换的位数给定*值*自变量的以 null 结尾的字符串并将结果存储 (最多 33 个字符 **_itoa**， **_ltoa**，和 **_ultoa**，并为 65 **_i64toa**并 **_ui64toa**) 中*缓冲区*。 如果*基数*等于 10 并*值*是负数，存储字符串的第一个字符为减号 (**-**)。 **_Itow**， **_ltow**， **_ultow**， **_i64tow**，并 **_ui64tow**函数都是宽字符新版 **_itoa**， **_ltoa**， **_ultoa**， **_i64toa**，并 **_ui64toa**，分别。

> [!IMPORTANT]
> 这些函数可以写入的缓冲区太小或结尾。 若要防止缓冲区溢出，请确保*缓冲区*足够大以容纳转换后的数字加上尾随的 null 字符和符号字符。 在代码中，不恰当使用的这些函数可能会导致严重的安全问题。

由于其潜在的安全问题，默认情况下，这些函数会导致弃用警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md):**此函数或变量可能不安全。请考虑使用** *safe_function* **相反。若要禁用弃用，请使用 _CRT_SECURE_NO_WARNINGS。** 我们建议你更改源代码以使用*safe_function*建议的警告消息。 更安全的函数不写入的字符数大于指定的缓冲区大小。 有关详细信息，请参阅[_itoa_s、 _itow_s 函数](itoa-s-itow-s.md)。

若要使用这些功能而无需弃用警告，定义 **_CRT_SECURE_NO_WARNINGS**包含任何 CRT 标头之前预处理器宏。 你可以执行此操作开发人员命令提示中的命令行通过添加 **/D_CRT_SECURE_NO_WARNINGS**编译器选项**cl**命令。 否则，在源文件中定义的宏。 如果使用预编译标头，定义顶部预编译标头的宏包括文件，通常 stdafx.h。 若要在源代码中定义的宏，请使用 **#define**指令之前包括任何 CRT 标头，如本例所示：

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

在C++，这些函数具有模板重载，调用其更安全的版本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

Posix 名称**itoa**， **ltoa**，并**ultoa**作为别名存在 **_itoa**， **_ltoa**，和 **_ultoa**函数。 Posix 名称已弃用，因为它们不遵循特定于实现的函数名称约定的 ISO c。默认情况下，这些函数会导致弃用警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md):**此项的 POSIX 名称已弃用。请改用 ISO C 和C++一致的名称：** *new_name*。 我们建议你更改源代码才能使用这些函数的更安全版本 **_itoa_s**， **_ltoa_s**，或 **_ultoa_s**。 有关详细信息，请参阅[_itoa_s、 _itow_s 函数](itoa-s-itow-s.md)。

源代码可移植性，您可能想要保留在代码中的 Posix 名称。 若要使用这些功能而无需弃用警告，可以同时定义 **_CRT_NONSTDC_NO_WARNINGS**并 **_CRT_SECURE_NO_WARNINGS**包含任何 CRT 标头之前预处理器宏。 你可以执行此操作开发人员命令提示中的命令行通过添加 **/D_CRT_SECURE_NO_WARNINGS**并 **/D_CRT_NONSTDC_NO_WARNINGS**编译器选项，到**cl**命令。 否则，在源文件中定义的宏。 如果使用预编译标头，定义顶部预编译标头的宏包括文件中，通常 stdafx.h。 若要在源代码中定义的宏，请使用 **#define**指令之前包括任何 CRT 标头，如本例所示：

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大转换计数宏

为了帮助您创建的安全缓冲区的转换，CRT 包括一些方便的宏。 这些定义的转换每个整数类型，包括 null 终止符的最长的可能值所需的缓冲区大小，并登录字符，为几个常见的基准。 若要确保转换缓冲区足够大，接收任何转换中指定的基*基数*，使用其中一种定义宏时分配的缓冲区。 这有助于防止缓冲区溢出错误时将整型类型转换为字符串。 在您的源中包括 stdlib.h 或 wchar.h 时定义这些宏。

若要使用这些宏之一的字符串转换函数中，声明转换缓冲区的合适的字符类型和宏值的整数类型和基用作缓冲区维度。 此表列出了适用于每个函数列出基本的宏：

||||
|-|-|-|
|函数|radix|宏|
|**_itoa**， **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**， **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**， **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**， **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**， **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

此示例中使用转换计数宏来定义缓冲区大小正好能容纳**无符号长长**基 2 中：

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

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**itoa**， **ltoa**， **ultoa**|\<stdlib.h>|
|**_itoa**， **_ltoa**， **_ultoa**， **_i64toa**， **_ui64toa**|\<stdlib.h>|
|**_itow**， **_ltow**， **_ultow**， **_i64tow**， **_ui64tow**|\<stdlib.h> 或 \<wchar.h>|

这些函数和宏是特定于 Microsoft 的。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此示例演示一些整数转换函数的使用。 请注意，使用 **_CRT_SECURE_NO_WARNINGS**宏提示警告 C4996。

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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s、 _itow_s 函数](itoa-s-itow-s.md)<br/>
