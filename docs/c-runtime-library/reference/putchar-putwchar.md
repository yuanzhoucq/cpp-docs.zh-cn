---
title: putchar、putwchar
ms.date: 4/2/2020
api_name:
- putchar
- putwchar
- _o_putchar
- _o_putwchar
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putchar
- putwchar
- _puttchar
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
ms.openlocfilehash: 09ad53a7f4e953da05d7eafd6662bf250731b5d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333131"
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

*C*<br/>
要写入的字符。

## <a name="return-value"></a>返回值

返回写入的字符。 要指示错误或文件结尾条件 **，putc**和**putchar**返回**EOF**;**普wc**和**普瓦查尔**返回**WEOF。** 对于所有四种例程，使用 [ferror](ferror.md) 或 [feof](feof.md) 来检查是否存在错误或文件结尾。 如果传递*了流的*空指针，这些函数将生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回**EOF**或**WEOF**并将**errno**设置为**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**putc**例程将单个字符*c*写入当前位置的输出*流*。 任何整数都可以传递给**putc，** 但只写入较低的 8 位。 **putchar**例程与`putc( c, stdout )`相同。 对于每个例程，如果发生读取错误，则会设置流的错误指示器。 **putc**和**putchar**分别类似于**fputc**和 **_fputchar，** 但作为函数和宏实现（请参阅[在函数和宏之间进行选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)）。 **putwc**和**putwchar**分别是 putc 和**putchar**的宽字符版本。 **putchar**

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 它们可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 （UWP） 应用中不支持该控制台。 在与控制台 **、stdin、stdout**和**stder**关联的标准流句柄必须重定向，C 运行时函数才能在 UWP 应用中使用它们。 **stdout** 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
