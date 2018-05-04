---
title: clearerr | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- clearerr
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
- clearerr
dev_langs:
- C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c78355277fbb987d82bed46fb0b5f4ffd848b6a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="clearerr"></a>clearerr

重置流的错误指示符。 提供此函数的一个更安全的版本；请参阅 [clearerr_s](clearerr-s.md)。

## <a name="syntax"></a>语法

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*指向**文件**结构。

## <a name="remarks"></a>备注

**Clearerr**函数重置错误指示器和的文件尾指示器*流*。 错误指示符不自动清除;设置指定的流的错误指示器后，该流上继续执行操作来返回之前的错误值**clearerr**， [fseek](fseek-fseeki64.md)， **fsetpos**，或[rewind](rewind.md)调用。

如果*流*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回。 有关详细信息**errno**和错误代码，请参阅[errno 常量](../../c-runtime-library/errno-constants.md)。

提供此函数的一个更安全的版本；请参阅 [clearerr_s](clearerr-s.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

```Output

n

```

```Output

      nWrite error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>请参阅

[错误处理](../../c-runtime-library/error-handling-crt.md)<br/>
[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
