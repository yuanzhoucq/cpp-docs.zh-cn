---
title: fgetc、fgetwc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
dev_langs:
- C++
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f06c5c2f092932d97755a8f0cff63cde3a9682c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fgetc-fgetwc"></a>fgetc、fgetwc

从流中读取字符。

## <a name="syntax"></a>语法

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fgetc**返回作为读取的字符**int**或返回**EOF**以指示错误或文件结尾。 **fgetwc**返回时，作为[wint_t](../../c-runtime-library/standard-types.md)，对应于读取的字符或返回的宽字符**WEOF**以指示错误或文件结尾。 对于这两个函数中，使用**feof**或**ferror**来区分错误和文件尾条件。 如果发生读取错误，则会设置流的错误指示器。 如果*流*是**NULL**， **fgetc**和**fgetwc**中所述将调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**EOF**。

## <a name="remarks"></a>备注

其中每个函数从与关联的文件的当前位置读取单个字符*流*。 然后该函数递增关联的文件指针（如果已定义）以指向下一个字符。 如果流位于文件结尾，则设置流的文件结尾指示器。

**fgetc**等效于**getc**，但仅作为函数，而不是作为函数和宏实现。

**fgetwc**是宽字符版本的**fgetc**; 它读取**c**作为多字节字符或宽字符根据是否*流*中打开文本模式还是二进制模式。

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。

有关在文本模式和二进制模式中处理宽字符和多字节字符的详细信息，请参阅[文本模式和二进制模式中的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetctxt"></a>输入：crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>输出

```Output
Line one.
Line two.
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
