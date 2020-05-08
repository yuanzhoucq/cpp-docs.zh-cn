---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 907d02e94c79acf09dfa99a8b42e9f448d32dcfa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915754"
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

*宽限*<br/>
用户分配的缓冲区。

*mode*<br/>
缓冲模式。

size <br/>
缓冲区大小（以字节为单位）。 允许的范围： 2 <= *size* <= INT_MAX （2147483647）。 在内部，为*size*提供的值将向下舍入为最接近的2的倍数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

如果*stream*为**NULL**，或者*模式*或*大小*不在有效的更改范围内，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 -1 并将 errno 设置为 EINVAL********。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Setvbuf**函数允许程序控制*流*的缓冲和缓冲区大小。 *流*必须引用打开的文件，该文件在打开后尚未完成 i/o 操作。 *缓冲区*所指向的数组将用作缓冲区，除非它为**NULL**，在这种情况下， **setvbuf**将使用自动分配的长度为*大小*为/ \* 2 字节的缓冲区。

模式必须为 **_IOFBF**、 **_IOLBF**或 **_IONBF**。 如果*模式*为 **_IOFBF**或 **_IOLBF**，则使用*size*作为缓冲区的大小。 如果 **_IONBF***模式*，则流将不缓冲，并忽略*大小*和*缓冲区*。 *模式*的值及其含义如下：

|*模式*值|含义|
|-|-|
| **_IOFBF** | 完全缓冲;也就是说，将使用*缓冲区*作为缓冲区大小，并将*大小*用作缓冲区的大小。 如果*缓冲区*为**NULL**，则将使用自动分配的缓冲区*大小*（long）。 |
| **_IOLBF** | 对于某些系统，会提供行缓冲。 但对于 Win32，行为与 **_IOFBF**完全缓冲相同。 |
| **_IONBF** | 无论*缓冲区*或*大小*如何，都不使用任何缓冲区。 |

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
