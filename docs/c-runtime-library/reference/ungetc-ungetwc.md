---
title: ungetc、ungetwc
ms.date: 11/04/2016
api_name:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: f3b6c6ed3fe8ff5976afa1da2ed437e25c923b99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957420"
---
# <a name="ungetc-ungetwc"></a>ungetc、ungetwc

将字符重新推送到流上。

## <a name="syntax"></a>语法

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*c*<br/>
要推送的字符。

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

如果成功，则每个函数将返回字符参数*c*。 如果无法向后推送*c* ，或者未读取任何字符，则输入流将保持不变，并且**ungetc**返回**EOF**;**ungetwc**返回**WEOF**。 如果*stream*为**NULL**，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回**EOF**或**WEOF** ，并将**errno**设置为**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Ungetc**函数将字符*c*推送到*stream*上，并清除文件尾指示符。 流必须打开以供读取。 *对流*的后续读取操作以*c*开头。 将忽略使用**ungetc**将**EOF**推送到流的尝试。

如果在从流中读取字符之前调用了**fflush**、 [fseek](fseek-fseeki64.md)、 **fsetpos**或[倒带](rewind.md)，则可能会清除**ungetc**上放置的字符。 文件位置指示符将拥有将字符推送回之前的值。 对应流的外部存储未改变。 对文本流进行成功的**ungetc**调用时，将不指定文件位置指示符，直到读取或丢弃所有推回的字符。 对于二进制流，每个成功的**ungetc**调用都将减少文件位置指示器;如果调用前其值为0，则调用后不定义该值。

如果两次调用之间没有读取或文件定位操作 **，则结果**是不可预知的。 调用**fscanf**后，对**ungetc**的调用可能会失败，除非已执行其他读取操作（例如**getc**）。 这是因为， **fscanf**本身调用了**ungetc**。

**ungetwc**是**ungetc**的宽字符版本。 但是，在每个针对文本或二进制流的成功**ungetwc**调用中，文件位置指示器的值是未指定的，直到读取或丢弃所有推送后的字符。

这些函数线程安全并会在执行期间锁定敏感数据。 有关非锁定版本，请参阅 [_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台、 **stdin**、 **stdout**和**stderr**关联的标准流句柄必须重定向, 然后 C 运行时函数才能在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
