---
title: feof | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- feof
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
- feof
dev_langs:
- C++
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3162fd72acdfedc198764a92deec043cd681a10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="feof"></a>feof

测试流的文件尾。

## <a name="syntax"></a>语法

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**Feof**如果读取的操作已尝试读取文件的末尾，函数将返回一个非零值; 否则，它返回 0。 如果流指针位于**NULL**，函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和**feof**返回 0。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Feof**例程 （同时作为函数和宏实现） 确定是否末尾*流*已传递。 当传递的文件结束时，读取操作返回文件尾指示器，直到流已关闭，或者直到[rewind](rewind.md)， **fsetpos**， [fseek](fseek-fseeki64.md)，或**clearerr**针对其调用。

例如，如果文件包含 10 个字节，并从文件读取 10 个字节**feof**将返回 0，因为即使文件指针是在文件末尾，已不尝试超出末尾。 仅尝试读取后将会第 11 个字节**feof**返回非零值。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**feof**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crtfeoftxt"></a>输入：crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>输出

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>请参阅

[错误处理](../../c-runtime-library/error-handling-crt.md)<br/>
[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
