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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ec5af25070e253f6c04d1aab13404306251ed716
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912695"
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

*宽限*<br/>
数据的存储位置。

size <br/>
项目大小（以字节为单位）。

*计数*<br/>
要读取的项的最大数量。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fread**返回实际读取的完整项的数量，如果发生错误，或者在到达*计数*之前遇到文件末尾，则此值可能小于*计数*。 使用**feof**或**ferror**函数将读取错误与文件结尾条件区分开来。 如果*大小*或*计数*为0，则**fread**将返回0，并且缓冲区内容将保持不变。 如果*流*或*缓冲区*是 null 指针， **fread**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL** ，并返回0。

有关这些错误代码的详细信息，请参阅[ \_doserrno、errno、 \_sys\_errlist 和\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>备注

**Fread**函数从输入*流*中读取的*大小*为字节*的项，并将其*存储在*缓冲区*中。 与*流*关联的文件指针（如果有）以实际读取的字节数为增量增加。 如果在[文本模式下](../../c-runtime-library/text-and-binary-mode-file-i-o.md)打开给定的流，则会将 Windows 样式的换行符转换为 Unix 样式的换行符。 也就是说，回车换行符（CRLF）对替换为单行换行符（LF）字符。 该替换不会影响文件指针或返回值。 如果发生错误，文件指针位置不确定。 无法确定部分读取项的值。

在文本模式流上使用时，如果所请求的数据量（即，*大小* \* *计数*）大于或等于内部**文件** \*缓冲区大小（默认为4096字节，可通过使用[setvbuf](../../c-runtime-library/reference/setvbuf.md)进行配置），则流数据直接复制到用户提供的缓冲区中，并在该缓冲区中完成行转换。 由于转换后的数据可能比复制到缓冲区中的流数据短，因此，超过*缓冲区*\[*return_value* \* *大小*] （其中*return_value*是**fread**中的返回值）可能包含文件中未转换的数据。 出于此原因，我们建议你在*缓冲区*\[*return_value* \* *大小*为的情况下，以 null 终止字符数据; 如果缓冲区的目的是要充当 C 样式字符串，则为。 有关文本模式和二进制模式效果的详细信息，请参阅[fopen](fopen-wfopen.md) 。

此函数将锁定其他线程。 如果需要非锁定版本，请使用 **_fread_nolock**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
[文本和二进制文件 i/o](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
