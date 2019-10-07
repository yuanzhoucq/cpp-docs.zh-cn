---
title: _fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l
ms.date: 11/04/2016
api_name:
- _fwprintf_p
- _fprintf_p_l
- _fwprintf_p_l
- _fprintf_p
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fprintf_p
- _ftprintf_p
- fwprintf_p
- _fwprintf_p
- fprintf_p
- ftprintf_p
helpviewer_keywords:
- fprintf_p_l function
- fprintf_p function
- _fprintf_p_l function
- _fprintf_p function
- _ftprintf_p_l function
- streams, printing formatted data to
- _fwprintf_p function
- fwprintf_p function
- _ftprintf_p function
- _fwprintf_p_l function
- ftprintf_p function
- printing [C++], formatted data to streams
- ftprintf_p_l function
- fwprintf_p_l function
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
ms.openlocfilehash: 6509aba4097b3b37443443b533ebd9fb92c923a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957000"
---
# <a name="_fprintf_p-_fprintf_p_l-_fwprintf_p-_fwprintf_p_l"></a>_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l

将格式化数据输出到流。

## <a name="syntax"></a>语法

```C
int _fprintf_p(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fprintf_p_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int _fwprintf_p(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwprintf_p_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>参数

*stream*<br/>
指向**文件**结构的指针。

*format*<br/>
窗体控件字符串。

*实际*<br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

当发生输出错误时， **_fprintf_p**和 **_fwprintf_p**返回写入的字符数或返回一个负值。

## <a name="remarks"></a>备注

**_fprintf_p**设置格式并将一系列字符和值输出到输出*流*中。 每个函数*参数*（如果有）根据*格式*规范的相应格式规范进行转换和输出。 对于 **_fprintf_p**，*格式*参数具有相同的语法，并使用它在 **_printf_p**中。 这些函数支持位置参数，即可以更改格式字符串所使用的参数顺序。 有关位置参数的详细信息，请参阅 [printf_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。

**_fwprintf_p**是 **_fprintf_p**的宽字符版本;在 **_fwprintf_p**中， *format*是宽字符字符串。 如果在 ANSI 模式下打开流，则这些函数行为相同。 **_fprintf_p**当前不支持输出到 UNICODE 流中。

使用 **_l**后缀的这些函数的版本是相同的，只不过它们使用传入的区域设置参数而不是当前区域设置。

> [!IMPORTANT]
> 确保 format不是用户定义的字符串。

与不安全版本一样（请参阅[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)），这些函数将验证其参数并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述，如果有一个*流*或*format*为空指针，或者如果有任何未知或格式不正确的格式说明符，则为。 如果允许执行继续，则函数将返回-1，并将**errno**设置为**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_ftprintf_p**|**_fprintf_p**|**_fprintf_p**|**_fwprintf_p**|
|**_ftprintf_p_l**|**_fprintf_p_l**|**_fprintf_p_l**|**_fwprintf_p_l**|

有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fprintf_p**、 **_fprintf_p_l**|\<stdio.h>|
|**_fwprintf_p**、 **_fwprintf_p_l**|\<stdio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fprintf_p.c
// This program uses _fprintf_p to format various
// data and print it to the file named FPRINTF_P.OUT. It
// then displays FPRINTF_P.OUT on the screen using the system
// function to invoke the operating-system TYPE command.
//

#include <stdio.h>
#include <process.h>

int main( void )
{
    FILE    *stream = NULL;
    int     i = 10;
    double  fp = 1.5;
    char    s[] = "this is a string";
    char    c = '\n';

    // Open the file
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)
    {
        // Format and print data
        _fprintf_p( stream, "%2$s%1$c", c, s );
        _fprintf_p( stream, "%d\n", i );
        _fprintf_p( stream, "%f\n", fp );

        // Close the file
        fclose( stream );
    }

    // Verify our data
    system( "type fprintf_p.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[printf_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)<br/>
[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
