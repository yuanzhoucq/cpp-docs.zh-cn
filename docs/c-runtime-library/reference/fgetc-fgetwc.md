---
title: fgetc、fgetwc
ms.date: 4/2/2020
api_name:
- fgetwc
- fgetc
- _o_fgetc
- _o_fgetwc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fgettc
- fgetwc
- fgetc
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
ms.openlocfilehash: 5f8d4b1fcdc2d4d4de712ee79742025db74b6452
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189280"
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

**fgetc**返回作为读取的字符， **`int`** 或返回**EOF**以指示错误或文件尾。 **fgetwc**以[wint_t](../../c-runtime-library/standard-types.md)的形式返回与读取字符对应的宽字符，或者返回**WEOF**以指示错误或文件尾。 对于这两个函数，请使用**feof**或**ferror**来区分错误和文件尾条件。 如果发生读取错误，则会设置流的错误指示器。 如果*stream*为**NULL**，则**fgetc**和**fgetwc**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**并返回**EOF**。

## <a name="remarks"></a>备注

其中每个函数均从与*stream*关联的文件的当前位置读取单个字符。 然后该函数递增关联的文件指针（如果已定义）以指向下一个字符。 如果流位于文件结尾，则设置流的文件结尾指示器。

**fgetc**等效于**getc**，但仅作为函数实现，而不是作为函数和宏实现。

**fgetwc**是**fgetc**的宽字符版本;它根据*流*是在文本模式还是二进制模式中打开，将**c**读取为多字节字符或宽字符。

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。

有关在文本模式和二进制模式中处理宽字符和多字节字符的详细信息，请参阅[文本模式和二进制模式中的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="input-crt_fgetctxt"></a>输入：crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
