---
title: _vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vsprintf_p
- _vswprintf_p
- _vsprintf_p_l
- _vswprintf_p_l
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
apitype: DLLExport
f1_keywords:
- vsprintf_p
- _vswprintf_p
- _vstprintf_p
- vswprintf_p
- _vsprintf_p
- vstprintf_p
dev_langs:
- C++
helpviewer_keywords:
- vstprintf_p_l function
- _vsprintf_p_l function
- _vstprintf_p function
- vsprintf_p_l function
- _vswprintf_p function
- vswprintf_p function
- vsprintf_p function
- vswprintf_p_l function
- _vswprintf_p_l function
- vstprintf_p function
- formatted text [C++]
- _vsprintf_p function
- _vstprintf_p_l function
ms.assetid: 00821c0d-9fee-4d8a-836c-0669cfb11317
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab2c33301f5746065e46dcba9f166679a330c98f
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="vsprintfp-vsprintfpl-vswprintfp-vswprintfpl"></a>_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l

使用指向自变量列表的指针编写格式化输出，并且能够指定自变量的使用顺序。

## <a name="syntax"></a>语法

```C
int _vsprintf_p(
   char *buffer,
   size_t sizeInBytes,
   const char *format,
   va_list argptr
);
int _vsprintf_p_l(
   char *buffer,
   size_t sizeInBytes,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vswprintf_p(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_p_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
输出的存储位置

*sizeInBytes*<br/>
大小*缓冲区*以字符为单位。

*count*<br/>
要存储在 Unicode 版的此函数中的最大字符数。

*format*<br/>
格式规范。

*argptr*<br/>
指向参数列表的指针。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_vsprintf_p**和 **_vswprintf_p**返回写入的字符数，不包括终止 null 字符或为负值，如果发生输出错误。

## <a name="remarks"></a>备注

其中每个函数采用指向自变量列表，然后设置格式和指向的内存中写入给定的数据*缓冲区*。

这些函数与不同**vsprintf_s**和**vswprintf_s**仅在于后者支持位置参数。 有关详细信息，请参阅 [printf_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。

使用这些函数的版本 **_l**后缀是相同，只不过它们使用传递而不是当前线程区域设置的区域设置参数。

如果*缓冲区*或*格式*参数**NULL**指针，如果计数为零，或如果格式字符串包含无效的格式设置字符，无效的参数调用处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回-1 并设置**errno**到**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstprintf_p**|**_vsprintf_p**|**_vsprintf_p**|**_vswprintf_p**|
|**_vstprintf_p_l**|**_vsprintf_p_l**|**_vsprintf_p_l**|**_vswprintf_p_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_vsprintf_p**， **_vsprintf_p_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vswprintf_p**， **_vswprintf_p_l**|\<stdio.h> 或 \<wchar.h> 和 \<stdarg.h>|\<varargs.h>*|

\* 仅对 UNIX V 兼容性是必需的。

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt__vsprintf_p.c
// This program uses vsprintf_p to write to a buffer.
// The size of the buffer is determined by _vscprintf_p.

#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void example( char * format, ... )
{
    va_list  args;
    int      len;
    char     *buffer = NULL;

    va_start( args, format );

    // _vscprintf doesn't count the
    // null terminating string so we add 1.
    len = _vscprintf_p( format, args ) + 1;

    // Allocate memory for our buffer
    buffer = (char*)malloc( len * sizeof(char) );
    if (buffer)
    {
        _vsprintf_p( buffer, len, format, args );
        puts( buffer );
        free( buffer );
    }
    va_end( args );
}

int main( void )
{
    // First example
    example( "%2$d %1$c %3$d", '<', 123, 456 );

    // Second example
    example( "%s", "This is a string" );
}
```

```Output
123 < 456
This is a string
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函数](../../c-runtime-library/vprintf-functions.md)<br/>
[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
