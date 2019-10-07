---
title: _itoa，_itow 函数
ms.date: 08/19/2019
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
ms.openlocfilehash: 97085ab8a8c720d278374868f9b1c90a91a6da3b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953569"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa、_itoa、ltoa、_ltoa、ultoa、_ultoa、_i64toa、_ui64toa、_itow、_ltow、_ultow、_i64tow、_ui64tow

将整数转换为字符串。 提供这些函数的更多安全版本;请参阅[_itoa_s、_itow_s 函数](itoa-s-itow-s.md)。

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

*value*<br/>
要转换的数字。

*buffer*<br/>
保存转换结果的缓冲区。

*radix*<br/>
用于转换值的基数，*该值*必须在2-36 范围内。

*size*<br/>
缓冲区的长度（以字符类型的单位表示）。 此参数是从中C++的*buffer*参数推断出来的。

## <a name="return-value"></a>返回值

其中每个函数均返回一个指向*缓冲区*的指针。 无错误返回。

## <a name="remarks"></a>备注

**_Itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**和 **_ui64toa**函数将给定*值*参数的数字转换为以 null 结尾的字符串，并存储结果（最多33个字符用于 **_itoa）** 、 **_ltoa**和 **_ultoa**以及65，用于 **_i64toa**和 **_ui64toa**）。 如果*基数*等于10并且*值*为负，则存储字符串的第一个字符为减号（ **-** ）。 **_Itow**、 **_ltow**、 **_ultow**、 **_i64tow**和 **_ui64tow**函数分别是 **_itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**和 **_ui64toa**的宽字符版本。

> [!IMPORTANT]
> 这些函数可以写入超过太小缓冲区末尾的部分。 若要防止缓冲区溢出，请确保*缓冲区*的大小足以容纳转换后的数字加上尾随的 null 字符和符号字符。 这些函数的误用可能导致代码中出现严重的安全问题。

由于可能存在安全问题，因此默认情况下，这些函数会导致弃用警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)：**此函数或变量可能不安全。请考虑改用** *safe_function* **。若要禁用弃用，请使用 _CRT_SECURE_NO_WARNINGS。** 建议更改源代码，以使用警告消息建议的 *safe_function* 。 更安全的函数不能写入超过指定缓冲区大小的字符。 有关详细信息，请参阅[_itoa_s、_itow_s 函数](itoa-s-itow-s.md)。

若要在不使用弃用警告的情况下使用这些函数，请在包含任何 CRT 标头之前定义 **_CRT_SECURE_NO_WARNINGS**预处理器宏。 可以在开发人员命令提示符下的命令行中执行此操作，方法是将 **/D_CRT_SECURE_NO_WARNINGS**编译器选项添加到**cl**命令。 否则，在源文件中定义宏。 如果使用预编译标头，请在预编译标头包含文件、 *pch* （Visual Studio 2017 及更早版本）的顶部定义宏（*stdafx.h* ）。 若要在源代码中定义宏，请在包含任何 CRT 标头之前使用 **#define**指令，如以下示例中所示：

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

在C++中，这些函数具有调用更安全的副本的模板重载。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

Posix 名称**itoa**、 **ltoa**和**ultoa**作为 **_itoa**、 **_ltoa**和 **_ultoa**函数的别名存在。 Posix 名称已弃用，因为它们不遵循 ISO C 的特定于实现的函数名约定。默认情况下，这些函数会导致弃用警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)：**此项的 POSIX 名称已弃用。请改用 ISO C 和C++相容名称：** *new_name*。 建议更改源代码，以使用这些函数的更安全版本 **_itoa_s**、 **_ltoa_s**或 **_ultoa_s**。 有关详细信息，请参阅[_itoa_s、_itow_s 函数](itoa-s-itow-s.md)。

对于源代码可移植性，你可能想要在代码中保留 Posix 名称。 若要在不使用弃用警告的情况下使用这些函数，请在包含任何 CRT 标头之前同时定义 **_CRT_NONSTDC_NO_WARNINGS**和 **_CRT_SECURE_NO_WARNINGS**预处理器宏。 可在开发人员命令提示符下的命令行中执行此操作，方法是将 **/D_CRT_SECURE_NO_WARNINGS**和 **/D_CRT_NONSTDC_NO_WARNINGS**编译器选项添加到**cl**命令。 否则，在源文件中定义宏。 如果使用预编译标头，请在预编译头包含文件的顶部定义宏。 若要在源代码中定义宏，请在包含任何 CRT 标头之前使用 **#define**指令，如以下示例中所示：

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大转换计数宏

为了帮助您为转换创建安全缓冲区，CRT 包含了一些便利的宏。 它们定义了转换若干公共基类型的每个整数类型的最大可能值（包括 null 结束符和符号字符）所需的缓冲区大小。 若要确保转换缓冲区足够大，以便在*基数*指定的基础中接收任何转换，请在分配缓冲区时使用其中一个已定义的宏。 这有助于防止在将整型类型转换为字符串时出现缓冲区溢出错误。 当你在源中包括 stdlib.h 或 wchar 时，将定义这些宏。

若要在字符串转换函数中使用其中一种宏，请声明相应字符类型的转换缓冲区，并将该宏值用于 integer 类型，将 base 作为缓冲区维度。 此表列出了适用于所列基的每个函数的宏：

||||
|-|-|-|
|函数|radix|宏|
|**_itoa**、 **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**、 **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**、 **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**、 **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**、 **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

此示例使用转换计数宏来定义一个缓冲区，该缓冲区足以在 base 2 中包含**无符号长**时间：

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
|**itoa**、 **ltoa**、 **ultoa**|\<stdlib.h>|
|**_itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**、 **_ui64toa**|\<stdlib.h>|
|**_itow**、 **_ltow**、 **_ultow**、 **_i64tow**、 **_ui64tow**|\<stdlib.h> 或 \<wchar.h>|

这些函数和宏是 Microsoft 特定的。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此示例演示如何使用一些整数转换函数。 请注意， **_CRT_SECURE_NO_WARNINGS**宏的使用会使警告 C4996 静音。

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
[_itoa_s，_itow_s 函数](itoa-s-itow-s.md)<br/>
