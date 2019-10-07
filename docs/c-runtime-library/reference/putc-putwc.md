---
title: putc、putwc
ms.date: 11/04/2016
api_name:
- putwc
- putc
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _puttc
- putwc
- putc
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
ms.openlocfilehash: 2fcd0ea2263cd858b0b4ce855f96c0389956ccc3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950101"
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

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

返回写入的字符。 若要指示错误或文件尾条件， **putc**和**putchar**返回**EOF**;**putwc**和**putwchar**返回**WEOF**。 对于所有四种例程，使用 [ferror](ferror.md) 或 [feof](feof.md) 来检查是否存在错误或文件结尾。 如果为*stream*传递了 null 指针，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回**EOF**或**WEOF** ，并将**errno**设置为**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Putc**例程将单个字符*c*写入当前位置的输出*流*中。 任何整数都可以传递到**putc**，但仅写入较低的8位。 **Putchar**例程与完全相同`putc( c, stdout )`。 对于每个例程，如果发生读取错误，则会设置流的错误指示器。 **putc**和**putchar**分别与**fputc**和 **_fputchar**相似，但同时作为函数和宏实现（请参阅在[函数和宏之间选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)）。 **putwc**和**putwchar**分别是**putc**和**putchar**的宽字符版本。 如果在 ANSI 模式下打开流，则**putwc**和**putc**的行为相同。 **putc**当前不支持输出到 UNICODE 流中。

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

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台、 **stdin**、 **stdout**和**stderr**关联的标准流句柄必须重定向, 然后 C 运行时函数才能在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

### <a name="output"></a>Output

```Output
This is the line of output
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
