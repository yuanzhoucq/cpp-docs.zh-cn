---
title: _locking
ms.date: 4/2/2020
api_name:
- _locking
- _o__locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: c1c211ffaa63a0e4711374b01b0530ed8db20dfb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911539"
---
# <a name="_locking"></a>_locking

锁定或解锁文件的字节。

## <a name="syntax"></a>语法

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>参数

*fd*<br/>
文件描述符。

*mode*<br/>
要执行的锁定操作

*nbytes*<br/>
要锁定的字节数。

## <a name="return-value"></a>返回值

如果成功， **_locking**将返回0。 返回值-1 指示失败，在这种情况下， [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为以下值之一。

|errno 值|条件|
|-|-|
| **EACCES** | 锁定冲突（文件已锁定或已解锁）。 |
| **EBADF** | 无效的文件描述符。 |
| **EDEADLOCK** | 锁定冲突。 当指定 **_LK_LOCK**或 **_LK_RLCK**标志并且文件在10次尝试后无法锁定时返回。 |
| **EINVAL** | 为 **_locking**提供的参数无效。 |

如果失败是由错误参数导致，如无效的文件描述符，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

## <a name="remarks"></a>备注

**_Locking**函数锁定或解锁*fd*指定的文件的*nbytes*字节。 锁定文件中的字节将阻止其他进程访问这些字节。 所有锁定或解锁在文件指针的当前位置开始，并继续到接下来的 *nbytes* 字节。 可能会锁定超出文件尾的字节。

*mode* 必须是 Locking.h 中定义的以下清单常量之一。

|*模式*值|效果|
|-|-|
| **_LK_LOCK** | 锁定指定字节。 如果无法锁定字节，该程序会立即在 1 秒后再次尝试。 如果在 10 次尝试后仍无法锁定字节，该常量将返回一个错误。 |
| **_LK_NBLCK** | 锁定指定字节。 如果无法锁定字节，该常量将返回一个错误。 |
| **_LK_NBRLCK** | 与 **_LK_NBLCK**相同。 |
| **_LK_RLCK** | 与 **_LK_LOCK**相同。 |
| **_LK_UNLCK** | 要解锁的指定字节必须在之前锁定过。 |

可以锁定文件中不重叠的多个区域。 正在解锁的区域必须在之前锁定过。 **_locking**不会合并相邻区域;如果两个锁定区域相邻，则必须单独解锁每个区域。 区域应只是暂时锁定，在关闭文件或退出程序前应进行解锁。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h 1> 和 \<sys/locking.h 1>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crt_lockingtxt"></a>输入：crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>示例输出

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
