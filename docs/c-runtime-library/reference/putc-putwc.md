---
title: putc、putwc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putwc
- putc
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af5c6987f88238398a00e9da7f0d769f246ffc54
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211064"
---
# <a name="putc-putwc"></a>putc、putwc

将字符写入流。

## <a name="syntax"></a>语法

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*c*<br/>
要写入的字符。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

返回写入的字符。 若要指示错误或文件结尾条件**putc**并**putchar**返回 * * EOF`; **putwc`并**putwchar**返回**WEOF**。 对于所有四种例程，使用 [ferror](ferror.md) 或 [feof](feof.md) 来检查是否存在错误或文件结尾。 如果为传递 null 指针*流*，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回**EOF**或**WEOF**并设置**errno**到**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Putc**例程将单个字符写入*c*到输出*流*当前位置。 可以将任何整数传递给**putc**，但写入低 8 位。 **Putchar**例程等同于`putc( c, stdout )`。 对于每个例程，如果发生读取错误，则会设置流的错误指示器。 **putc**和**putchar**类似于**fputc**并 **_fputchar**分别，但同时作为函数和宏实现 (请参阅[选择函数和宏](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md))。 **putwc**并**putwchar**宽字符版本的**putc**并**putchar**分别。 **putwc**并**putc**如果在 ANSI 模式下打开流，则行为相同。 **putc**当前不到 UNICODE 流支持输出。

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 有关详细信息，请参阅 **_putc_nolock、_putwc_nolock**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，并**stderr**，C 运行时函数可以在 UWP 应用中使用它们之前，必须重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>输出

```Output
This is the line of output
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
