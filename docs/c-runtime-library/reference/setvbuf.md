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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 203265a8dd85854bcedd737359b856fdc4cce04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316263"
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

*缓冲区*<br/>
用户分配的缓冲区。

*模式*<br/>
缓冲模式。

*大小*<br/>
缓冲区大小（以字节为单位）。 允许范围：2 个<=*大小*<= INT_MAX （2147483647）。 在内部，为*大小*提供的值向下舍入到最接近的倍数 2。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

如果*流*为**NULL**，或者*模式*或*大小*不在有效的更改范围内，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 -1 并将 errno 设置为 EINVAL********。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**setvbuf**函数允许程序控制*流的*缓冲和缓冲区大小。 *流*必须引用自打开以来未经过 I/O 操作的打开文件。 *缓冲区*指向的数组用作缓冲区，除非它是**NULL，** 在这种情况下**setvbuf**使用长度*大小*/2 \* 2 字节的自动分配的缓冲区。

模式必须 **_IOFBF、_IOLBF****_IOLBF**或 **_IONBF**。 如果*模式***为_IOFBF**或 **_IOLBF**，则*大小*用作缓冲区的大小。 如果 *_IONBF模式***，则**流将取消缓冲，并忽略*大小*和*缓冲区*。 *模式*及其含义的值包括：

|*模式*值|含义|
|-|-|
| **_IOFBF** | 完全缓冲;也就是说，*缓冲区*用作缓冲区，*大小*用作缓冲区的大小。 如果*缓冲区*为**NULL，** 则使用自动分配的缓冲区*大小*字节长。 |
| **_IOLBF** | 对于某些系统，会提供行缓冲。 但是，对于 Win32，该行为与 **_IOFBF** - 完全缓冲相同。 |
| **_IONBF** | 无论缓冲区或*大小*如何，都不使用*缓冲区*。 |

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

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
