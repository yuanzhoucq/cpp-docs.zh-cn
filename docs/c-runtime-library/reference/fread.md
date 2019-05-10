---
title: fread
ms.date: 11/28/2018
apiname:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 7248eb08409b50d855dbb70c7638a856302b345b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287871"
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

*buffer*<br/>
数据的存储位置。

*size*<br/>
项目大小（以字节为单位）。

*count*<br/>
要读取的项的最大数量。

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fread**返回实际读取的完整项数，这可能是小于*计数*如果发生错误或到达之前遇到文件末尾*计数*。 使用**feof**或**ferror**函数以将读取的错误与文件结尾条件区分开来。 如果*大小*或*计数*为 0， **fread**返回 0 并且缓冲区内容保持不变。 如果*流*或*缓冲区*是 null 指针**fread**将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回 0。

请参阅[ \_doserrno，errno， \_sys\_errlist，并且\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)为这些错误代码的详细信息。

## <a name="remarks"></a>备注

**Fread**函数最多读取*计数*的项*大小*字节从输入*流*将其存储在*缓冲区*. 与关联的文件指针*流*（如果有） 为增量递增实际读取的字节数。 如果在打开给定的流[文本模式下](../../c-runtime-library/text-and-binary-mode-file-i-o.md)，Windows 样式换行符将转换为 Unix 样式换行符。 它是单一的换行 (LF) 字符替换回车符和换行符 (CRLF) 对。 该替换不会影响文件指针或返回值。 如果发生错误，文件指针位置不确定。 无法确定部分读取项的值。

如果请求的数据量上文本模式流，使用时 (即*大小* \* *计数*) 是大于或等于内部**文件** \*缓冲区大小 (默认情况下，这是 4096 个字节，可通过配置[setvbuf](../../c-runtime-library/reference/setvbuf.md))、 流数据直接复制到的用户提供的缓冲区，并且在该缓冲区中执行换行转换。 因为转换后的数据可能是短于流数据复制到缓冲区数据过去*缓冲区*\[*return_value* \* *大小*] (其中*return_value*是从返回的值**fread**) 可能包含文件中的未转换的数据。 出于此原因，我们建议您为 null 的终止字符数据在*缓冲区*\[*return_value* \* *大小*] 如果缓冲区的目的是将其用作 C 样式字符串。 请参阅[fopen](fopen-wfopen.md)有关效果的文本模式和二进制模式的详细信息。

此函数将锁定其他线程。 如果需要非锁定版本，使用 **_fread_nolock**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fread**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[文本和二进制文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
