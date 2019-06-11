---
title: scanf、_scanf_l、wscanf、_wscanf_l
ms.date: 11/04/2016
apiname:
- _wscanf_l
- scanf
- _scanf_l
- wscanf
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
- _tscanf
- _scanf_l
- wscanf
- _wscanf_l
- scanf
- _tscanf_l
helpviewer_keywords:
- tscanf_l function
- _tscanf_l function
- reading data [C++], from input streams
- _tscanf function
- data [C++], reading from input stream
- scanf_l function
- scanf function
- wscanf function
- _scanf_l function
- tscanf function
- formatted data [C++], from input streams
- wscanf_l function
- _wscanf_l function
ms.assetid: 73eac607-117f-4be4-9ff0-4afd9cf3c848
ms.openlocfilehash: 48aa0bb3348a3336de9ee0eb9f9ec0d3e1a2b3cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357117"
---
# <a name="scanf-scanfl-wscanf-wscanfl"></a>scanf、_scanf_l、wscanf、_wscanf_l

读取标准输入流中的格式化数据。 提供这些函数的更多安全版本；请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)。

## <a name="syntax"></a>语法

```C
int scanf(
   const char *format [,
   argument]...
);
int _scanf_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf(
   const wchar_t *format [,
   argument]...
);
int _wscanf_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>参数

*format*<br/>
格式控制字符串。

*argument*<br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回已成功转换和分配的字段数量；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。

如果*格式*是**NULL**调用指针，无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回**EOF**并设置**errno**到**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Scanf**函数从标准输入流中读取数据**stdin**并将数据写入到指定的位置*参数*。 每个*自变量*必须是指向类型中的类型说明符相对应的变量的指针*格式*。 如果复制出现在重叠的字符串之间，则该行为不确定。

> [!IMPORTANT]
> 读取的字符串时**scanf**，始终指定的宽度 **%s**格式 (例如， **"%32s"** 而不是 **"%s"** ); 否则为输入格式不正确很容易导致缓冲区溢出。 或者，可以考虑使用 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 或 [fgets](fgets-fgetws.md)。

**wscanf**是宽字符版本**scanf**;*格式*参数**wscanf**是宽字符字符串。 **wscanf**并**scanf**如果在 ANSI 模式下打开流，则行为相同。 **scanf**当前不支持 UNICODE 流的输入。

使用这些函数的版本 **_l**后缀完全相同，只不过它们使用传递中而不是当前线程区域设置的区域设置参数。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf**|**scanf**|**scanf**|**wscanf**|
|**_tscanf_l**|**_scanf_l**|**_scanf_l**|**_wscanf_l**|

有关详细信息，请参阅[格式规范字段 — scanf 函数和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**scanf**， **_scanf_l**|\<stdio.h>|
|**wscanf**， **_wscanf_l**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，并**stderr**，C 运行时函数可以在 UWP 应用中使用它们之前，必须重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_scanf.c
// compile with: /W3
// This program uses the scanf and wscanf functions
// to read formatted input.

#include <stdio.h>

int main( void )
{
   int   i, result;
   float fp;
   char  c, s[81];
   wchar_t wc, ws[81];
   result = scanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws ); // C4996
   // Note: scanf and wscanf are deprecated; consider using scanf_s and wscanf_s
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
   result = wscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws ); // C4996
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

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
