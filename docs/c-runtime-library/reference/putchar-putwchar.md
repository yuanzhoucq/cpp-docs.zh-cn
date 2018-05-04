---
title: putchar、putwchar | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putchar
- putwchar
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
- putchar
- putwchar
- _puttchar
dev_langs:
- C++
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7602ca44d6f8ec8197d1ebc61b4ef1d0847133f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="putchar-putwchar"></a>putchar、putwchar

将字符写入 **stdout**。

## <a name="syntax"></a>语法

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>参数

*c*<br/>
要写入的字符。

## <a name="return-value"></a>返回值

返回写入的字符。 以指示错误或文件尾条件**putc**和**putchar**返回 * * EOF`; **putwc`和**putwchar**返回**WEOF**。 对于所有四种例程，使用 [ferror](ferror.md) 或 [feof](feof.md) 来检查是否存在错误或文件结尾。 如果为传递 null 指针*流*，这些函数将生成无效的参数异常，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，它们将返回**EOF**或**WEOF**并设置**errno**到**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Putc**例程写入单个字符*c*到输出*流*当前位置处。 可以将任何整数传递给**putc**，但仅低 8 位写入。 **Putchar**例程等同于**putc (** * c ***，stdout)**。 对于每个例程，如果发生读取错误，则会设置流的错误指示器。 **putc**和**putchar**类似于**fputc**和 **_fputchar**分别，但同时作为函数和宏实现 (请参阅[选择函数和宏](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md))。 **putwc**和**putwchar**宽字符版本的**putc**和**putchar**分别。

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 它们可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，和**stderr**，必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_putchar.c
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

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putchar( *p );
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
