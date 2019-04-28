---
title: setvbuf
ms.date: 11/04/2016
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
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: d4336c6cc478a035fcc0b9b059a7161d58bc4442
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356311"
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

*stream*<br/>
指向**文件**结构的指针。

*buffer*<br/>
用户分配的缓冲区。

*模式*<br/>
缓冲模式。

*size*<br/>
缓冲区大小（以字节为单位）。 允许的范围：2 < =*大小*< = INT_MAX (2147483647)。 在内部，为提供的值*大小*向下舍入为 2 最接近倍数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

如果*流*是**NULL**，或者，如果*模式*或者*大小*是不在有效更改，无效参数处理程序调用，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则此函数将返回-1 并设置**errno**到**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Setvbuf**函数允许程序来控制这两种缓冲和缓冲区的大小*流*。 *流*必须引用打开的文件尚未进行 I/O 操作，因为它已打开。 指向的数组*缓冲区*用作缓冲区，除非它是**NULL**，在这种情况下**setvbuf**使用自动分配的缓冲区长度的*大小*/2 \* 2 个字节。

此模式必须是 **_IOFBF**， **_IOLBF**，或 **_IONBF**。 如果*模式下*是 **_IOFBF**或 **_IOLBF**，然后*大小*用作缓冲区的大小。 如果*模式下*是 **_IONBF**，该流是无缓冲并*大小*并*缓冲区*将被忽略。 值为*模式下*及其含义是：

|*模式*值|含义|
|-|-|
| **_IOFBF** | 完全缓冲;即*缓冲区*用作缓冲区并*大小*用作缓冲区的大小。 如果*缓冲区*是**NULL**，自动分配的缓冲区*大小*使用个字节长。 |
| **_IOLBF** | 对于某些系统，会提供行缓冲。 但是，对于 Win32，行为是相同 **_IOFBF** -完全缓冲。 |
| **_IONBF** | 不会使用缓冲区，而不考虑*缓冲区*或*大小*。 |

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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
