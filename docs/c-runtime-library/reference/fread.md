---
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346055"
---
# <a name="fread"></a>fread

从流读取数据。

## <a name="syntax"></a>语法

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*缓冲区*<br/>
数据的存储位置。

*大小*<br/>
项目大小（以字节为单位）。

*count*<br/>
要读取的项的最大数量。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fread**返回实际读取的完整项数，如果发生错误或在达到*计数*之前遇到文件结尾，则可能小于*计数*。 使用**feof**或**ferror**函数来区分读取错误和文件结尾条件。 如果*大小*或*计数*为 0，**则 fread**返回 0，缓冲区内容保持不变。 如果*流*或*缓冲区*是空指针，**则 fread**将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将**errno**设置到**EINVAL**并返回 0。

有关这些错误代码的详细信息[\_，请参阅剂量\_诺\_、errno、sys errlist 和\_sys\_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>备注

**fread**函数最多读取*以从输入流中计数**大小*字节项，*stream*并将其存储在*缓冲区*中。 与*流*关联的文件指针（如果有）由实际读取的字节数增加。 如果在[文本模式下](../../c-runtime-library/text-and-binary-mode-file-i-o.md)打开给定的流，Windows 样式的换行将转换为 Unix 样式的换行。 也就是说，滑车回线馈送 （CRLF） 对由单行馈送 （LF） 字符替换。 该替换不会影响文件指针或返回值。 如果发生错误，文件指针位置不确定。 无法确定部分读取项的值。

在文本模式流上使用时，如果请求的数据量（即*大小*\**计数*）大于或等于内部**FILE**\*缓冲区大小（默认情况下为 4096 字节，使用[setvbuf](../../c-runtime-library/reference/setvbuf.md)可配置），则流数据将直接复制到用户提供的缓冲区中，并在该缓冲区中完成换行。 由于转换后的数据可能比复制到缓冲区中的流数据短，因此超过*缓冲区*\[*的数据return_value*\**大小** （其中*return_value*是从**sread**返回值）可能包含文件中未转换的数据。 因此，如果缓冲区的意图用作 C 样式字符串，我们建议您在*缓冲区*\[*return_value*\**大小*下终止字符数据。 有关文本模式和二进制模式效果的详细信息，请参阅[fopen。](fopen-wfopen.md)

此函数将锁定其他线程。 如果需要非锁定版本，请使用 **_fread_nolock**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fread**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[文本和二进制文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
