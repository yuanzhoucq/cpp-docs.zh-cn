---
title: scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l
ms.date: 11/04/2016
apiname:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 0fcf2a9f3ac8585e71caa9f2cc990c7e303a2f5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528604"
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l

读取标准输入流中的格式化数据。 这些版本的 [scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>参数

*format*<br/>
格式控制字符串。

*自变量*<br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回已成功转换和分配的字段数量；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 返回值是**EOF**错误，或如果文件尾字符或字符串末尾字符时遇到的第一次尝试读取字符。 如果*格式*是**NULL**调用指针，无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**scanf_s**并**wscanf_s**返回**EOF**并设置**errno**到**EINVAL**.

有关这些及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Scanf_s**函数从标准输入流中读取数据**stdin**并将数据写入到由给定的位置*参数*。 每个*自变量*必须是指向类型中的类型说明符相对应的变量的指针*格式*。 如果在重叠的字符串之间发生复制，则此行为不确定。

**wscanf_s**是宽字符版本**scanf_s**;*格式*参数**wscanf_s**是宽字符字符串。 **wscanf_s**并**scanf_s**如果在 ANSI 模式下打开流，则行为相同。 **scanf_s**当前不支持 UNICODE 流的输入。

具有这些函数的版本 **_l**后缀完全相同，只不过它们使用传入的区域设置参数而不是当前线程区域设置。

与不同**scanf**并**wscanf**， **scanf_s**并**wscanf_s**中需要的所有输入类型参数指定的缓冲区大小**c**， **C**， **s**， **S**，或字符串中包含的控件集 **[]**。 字符形式的缓冲区大小作为额外参数，紧跟在指针后面传递到缓冲区或变量。 例如，如果您正在读取一个字符串，则将传递该字符串的缓冲区大小，如下所示：

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

缓冲区大小包括终止 null 字符。 您可以使用宽度规范字段来确保读入的标记可放入缓冲区中。 如果未使用任何宽度规范字段，并且读取的标记太大以致缓冲区中无法容纳，则不会向该缓冲区写入任何内容。

> [!NOTE]
> 大小参数的类型是**无符号**，而非**size_t**。 使用静态强制转换来转换**size_t**值设置为**无符号**64 位生成配置。

以下示例说明缓冲区大小参数描述的是最大字符数而非最大字节数。 在调用**wscanf_s**，指示缓冲区类型的字符宽度与所指示的格式说明符字符宽度不匹配。

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S**格式说明符表示使用的字符宽度"相反"支持的函数的默认宽度。 该字符宽度是单字节的，而函数支持双字节字符。 此示例可读入最多 9 个单字节宽度字符的字符串，并将其放入一个双字节宽度字符缓冲区中。 这些字符被视为单字节值；头两个字符存储在 `ws[0]` 中，紧接着的两个字符存储在 `ws[1]` 中，依此类推。

对于字符，可读取单个字符，如下所示：

```C
char c;
scanf_s("%c", &c, 1);
```

在读取非 null 终止的字符串的多个字符时，将整数用作宽度规范和缓冲区大小。

```C
char c[4];
scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated
```

有关详细信息，请参阅 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

有关详细信息，请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**scanf_s**， **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**， **_wscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，并**stderr**，C 运行时函数可以在 UWP 应用中使用它们之前，必须重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

当提供此输入时，该程序将生成以下输出：

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
