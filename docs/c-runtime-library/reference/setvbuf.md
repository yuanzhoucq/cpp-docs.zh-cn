---
title: setvbuf | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- setvbuf
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
- setvbuf
dev_langs:
- C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c5faca3ea3403ec06029e6c4a125915884621e4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="setvbuf"></a>setvbuf

控制流缓冲和缓冲区大小。

## <a name="syntax"></a>语法

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

*buffer*<br/>
用户分配的缓冲区。

*模式*<br/>
缓冲模式。

*size*<br/>
缓冲区大小（以字节为单位）。 允许范围： 2 < =*大小*< = INT_MAX (2147483647)。 在内部，为提供的值*大小*向下舍入到最接近的 2 的倍数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

如果*流*是**NULL**，或者如果*模式*或*大小*是不在有效的更改内的无效参数处理程序调用时中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将返回-1 并设置**errno**到**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Setvbuf**函数使程序能够控制这两个缓冲和缓冲区大小为*流*。 *流*必须引用尚未进行 I/O 操作，因为它已打开的打开文件。 指向数组*缓冲区*将用作缓冲区，除非它是**NULL**，在这种情况下**setvbuf**使用自动分配的缓冲区的长度*大小*  /2 * 2 个字节。

模式必须为 **_IOFBF**， **_IOLBF**，或 **_IONBF**。 如果*模式*是 **_IOFBF**或 **_IOLBF**，然后*大小*用作缓冲区的大小。 如果*模式*是 **_IONBF**，则流是无缓冲和*大小*和*缓冲区*将被忽略。 值为*模式*和其意义进行了：

|*模式*值|含义|
|-|-|
**_IOFBF**|完全缓冲;也就是说，*缓冲区*用作缓冲区和*大小*用作缓冲区的大小。 如果*缓冲区*是**NULL**，已自动分配的缓冲区*大小*使用字节长。
**_IOLBF**|对于某些系统，会提供行缓冲。 但是，对于 Win32 的行为是相同 **_IOFBF** -完全缓冲。
**_IONBF**|没有缓冲区使用，无论程序*缓冲区*或*大小*。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
