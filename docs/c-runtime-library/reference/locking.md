---
title: "_locking | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _locking
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
- _locking
dev_langs:
- C++
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0acd33e3f33077dafee9bd6c4892a17b42e7afe0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="locking"></a>_locking
锁定或解锁文件的字节。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fd`  
 文件描述符。  
  
 *模式*  
 要执行的锁定操作  
  
 *nbytes*  
 要锁定的字节数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `_locking` 返回 0。 返回值-1 指示失败，在这种情况下[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为以下值之一。  
  
 `EACCES`  
 锁定冲突（文件已锁定或已解锁）。  
  
 `EBADF`  
 无效的文件描述符。  
  
 `EDEADLOCK`  
 锁定冲突。 如果指定了 `_LK_LOCK` 或 `_LK_RLCK` 标志且该文件在尝试 10 次后仍无法锁定，则返回。  
  
 `EINVAL`  
 一个无效参数将提供给 `_locking`。  
  
 如果失败是由错误参数导致，如无效的文件描述符，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
## <a name="remarks"></a>备注  
 `_locking` 函数锁定或解锁由 `fd` 指定的文件的 *nbytes* 字节。 锁定文件中的字节将阻止其他进程访问这些字节。 所有锁定或解锁在文件指针的当前位置开始，并继续到接下来的 *nbytes* 字节。 可能会锁定超出文件尾的字节。  
  
 *mode* 必须是 Locking.h 中定义的以下清单常量之一。  
  
 `_LK_LOCK`  
 锁定指定字节。 如果无法锁定字节，该程序会立即在 1 秒后再次尝试。 如果在 10 次尝试后仍无法锁定字节，该常量将返回一个错误。  
  
 `_LK_NBLCK`  
 锁定指定字节。 如果无法锁定字节，该常量将返回一个错误。  
  
 `_LK_NBRLCK`  
 与 `_LK_NBLCK` 相同。  
  
 `_LK_RLCK`  
 与 `_LK_LOCK` 相同。  
  
 `_LK_UNLCK`  
 要解锁的指定字节必须在之前锁定过。  
  
 可以锁定文件中不重叠的多个区域。 正在解锁的区域必须在之前锁定过。 `_locking` 不会合并相邻区域；如果有两个相邻的锁定区域，每个区域必须单独解锁。 区域应只是暂时锁定，在关闭文件或退出程序前应进行解锁。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_locking`|\<io.h 1> 和 \<sys/locking.h 1>|\<errno.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
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
  
## <a name="input-crtlockingtxt"></a>输入：crt_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)