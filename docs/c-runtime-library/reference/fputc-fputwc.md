---
title: fputc、fputwc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af93e0c42002dc557f691daadd2fc003dced0247
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fputc-fputwc"></a>fputc、fputwc

将字符写入流。

## <a name="syntax"></a>语法

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
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

其中每个函数都会返回写入的字符。 有关**fputc**，返回值**EOF**指示错误。 有关**fputwc**，返回值**WEOF**指示错误。 如果*流*是**NULL**中, 所述，这些函数将调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，它们将返回**EOF**并设置**errno**到**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

其中每个函数将单个字符*c*到文件中的位置由关联的文件位置指示器 （如果已定义），并使提升根据指示器。 情况下**fputc**和**fputwc**，与关联文件*流*。 如果文件不支持定位请求，或在追加模式中打开，则该字符将被追加到流的末尾。

如果在 ANSI 模式下打开流，则这两个函数行为相同。 **fputc**当前不支持输出到 UNICODE 流。

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 有关详细信息，请参阅 [_fputc_nolock、_fputwc_nolock](fputc-nolock-fputwc-nolock.md)。

下面是例程特定的备注。

|例程|备注|
|-------------|-------------|
|**fputc**|等效于**putc**，但仅作为函数，而不是作为函数和宏实现。|
|**fputwc**|宽字符版本的**fputc**。 写入*c*作为多字节字符或宽字符根据是否*流*以文本模式还是二进制模式下打开。|

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台关联的标准流句柄-**stdin**， **stdout**，和**stderr**-必须将 C 运行时函数才能使用它们在 UWP 应用重定向. 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
