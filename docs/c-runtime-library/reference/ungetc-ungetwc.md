---
title: ungetc、ungetwc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9ce7de35118d4dd9c365b758a398b865e646036
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

如果成功，其中每个函数将返回字符自变量*c*。 如果*c*无法推送回或已不读取任何字符，如果输入的流保持不变并**ungetc**返回 * * EOF`; **ungetwc`返回**WEOF**。 如果*流*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**EOF**或**WEOF**返回和**errno**设置为**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Ungetc**函数将字符推送*c*回*流*并清除文件尾指示器。 流必须打开以供读取。 在进行的后续读取操作*流*开头*c*。 尝试推送**EOF**到流使用**ungetc**将被忽略。

字符放置在由流上**ungetc**是否可能清除**fflush**， [fseek](fseek-fseeki64.md)， **fsetpos**，或[rewind](rewind.md)之前从流读取字符时调用。 文件位置指示符将拥有将字符推送回之前的值。 对应流的外部存储未改变。 在成功**ungetc**直至所有读取或丢弃的推送回字符对文本流、 文件位置指示器的调用未指定。 在每个成功**ungetc**针对二进制流，文件位置指示器的调用是递减; 如果其值为 0 调用之前，未定义值调用的后面。

结果是不可预知如果**ungetc**两次未读取或文件定位操作之间的两个调用就调用。 调用了**fscanf**，调用**ungetc**可能失败，除非另一个读取操作 (如**getc**) 已执行。 这是因为**fscanf**本身调用**ungetc**。

**ungetwc**是宽字符版本的**ungetc**。 但是，在每个成功**ungetwc**是未指定的文本或二进制流中，文件位置指示器的值对的调用直到所有推送回字符被读取或被丢弃。

这些函数线程安全并会在执行期间锁定敏感数据。 有关非锁定版本，请参阅 [_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，和**stderr**，必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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
