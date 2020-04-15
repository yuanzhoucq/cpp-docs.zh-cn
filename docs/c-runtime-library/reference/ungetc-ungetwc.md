---
title: ungetc、ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
ms.openlocfilehash: 484af7b72f860a8a9d12cf0b62444871caad4675
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361295"
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

*C*<br/>
要推送的字符。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

如果成功，这些函数中的每一个都返回字符参数*c*。 如果*c*无法推回或未读取任何字符，则输入流保持不变 **，ungetc**将返回**EOF;****ungetwc**返回**WEOF。** 如果*流*为**NULL，** 则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回**EOF**或**WEOF，** 并将**errno**设置为**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**ungetc**函数将字符*c*推回*流*并清除文件结尾指示器。 流必须打开以供读取。 流*上的后续*读取操作从*c*开始。 忽略使用**ungetc**将**EOF**推送到流的尝试。

如果从流中读取字符之前调用 fflush、fseek、fsetpos**fsetpos**或[倒带](rewind.md)，则通过**ungetc**放置在流上的字符可能会被删除。 **fflush** [fseek](fseek-fseeki64.md) 文件位置指示符将拥有将字符推送回之前的值。 对应流的外部存储未改变。 在对文本流成功进行**ungetc**调用时，文件位置指示器未指定，直到读取或丢弃所有推回字符。 在针对二进制流的每个成功**ungetc**调用中，文件位置指示器都会递减;如果调用前的值为 0，则该值在调用后未定义。

如果两次调用**ungetc**时在两个调用之间没有读取或文件定位操作，则结果是不可预测的。 调用**fscanf**后，除非执行了另一个读取操作（如**getc），** 否则对**ungetc**的调用可能会失败。 这是因为**fscanf**本身调用**ungetc。**

**ungetwc**是一个宽字符版本的**ungetc。** 但是，在针对文本或二进制流的每个成功**ungetwc**调用中，文件位置指示器的值未指定，直到读取或丢弃所有推回字符。

这些函数线程安全并会在执行期间锁定敏感数据。 有关非锁定版本，请参阅 [_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 （UWP） 应用中不支持该控制台。 在与控制台 **、stdin、stdout**和**stder**关联的标准流句柄必须重定向，C 运行时函数才能在 UWP 应用中使用它们。 **stdout** 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
