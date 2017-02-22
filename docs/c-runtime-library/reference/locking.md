---
title: "_locking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_locking"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_locking"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_locking 函数"
  - "字节 [C++], 锁定文件"
  - "文件 [C++], 锁定"
  - "文件 [C++], 锁定字节"
  - "locking 函数"
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _locking
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

锁定或解锁文件的字节。  
  
## 语法  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### 参数  
 `fd`  
 文件说明符  
  
 *mode*  
 锁定要执行的操作。  
  
 *nbytes*  
 用于锁定的字节数。  
  
## 返回值  
 如果成功，`_locking`返回 0 。  为\-1的返回值指示一个错误，在[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为以下任一值情况下。  
  
 `EACCES`  
 锁定冲突 \(文件锁定或解除锁定\)。  
  
 `EBADF`  
 文件无效描述符。  
  
 `EDEADLOCK`  
 锁定冲突。  当 `_LK_LOCK` 或 `_LK_RLCK` 标志指定时和文件不可能被锁定，然后尝试10次之后返回。  
  
 `EINVAL`  
 无效参数指定 `_locking`。  
  
 如果失败由于参数错误，例如一个文件无效描述符，无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
## 备注  
 `_locking` 函数被锁定或解锁 `fd`指定文件的 *nbytes* 字节。  锁在文件的字节。其他进程可以防止对这些字节的访问权限。  所有锁定或解锁的起始文件指针的当前位置 *nbytes* 字节并为下运行。  锁定文件尾字节的过去是可能的。  
  
 清单常数*模式* 必须为下列之一，在 Locking.h 定义。  
  
 `_LK_LOCK`  
 锁定指定字节。  如果字节无法锁定，函数在 1 秒后直接调用。  如果10 多次尝试后字节无法锁定后，常数返回 FALSE。  
  
 `_LK_NBLCK`  
 锁定指定字节。  如果字节无法锁定，常数将返回 false。  
  
 `_LK_NBRLCK`  
 与 `_LK_NBLCK` 相同。  
  
 `_LK_RLCK`  
 与 `_LK_LOCK` 相同。  
  
 `_LK_UNLCK`  
 取消锁定指定字节，以前必须锁定。  
  
 重叠文件的多区域可以锁定。  绑定以前锁定解锁的区域。  `_locking` 不合并相邻区域；如果两种锁定的区域是连续的，必须单独取消锁定每个区域。  只应简要锁区域应在关闭文件或程序退出之前被取消锁定。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_locking`|\<io.h 和\> sys \<\/locking.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
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
  
## Input: crt\_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## 示例输出  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)