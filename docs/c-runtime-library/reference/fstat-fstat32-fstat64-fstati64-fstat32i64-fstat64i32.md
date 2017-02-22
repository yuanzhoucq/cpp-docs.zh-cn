---
title: "_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fstat32"
  - "_fstat64"
  - "_fstati64"
  - "_fstat"
  - "_fstat64i32"
  - "_fstat32i64"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_fstat32i64"
  - "fstat"
  - "fstat64i32"
  - "_fstat64"
  - "_fstati64"
  - "fstat64"
  - "_fstat32"
  - "fstat32i64"
  - "fstati64"
  - "_fstat"
  - "fstat32"
  - "_fstat64i32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstat64 函数"
  - "fstati64 函数"
  - "_fstat64i32 函数"
  - "_fstat32i64 函数"
  - "_fstat32 函数"
  - "文件信息"
  - "fstat64i32 函数"
  - "fstat32 函数"
  - "fstat 函数"
  - "fstat64 函数"
  - "_fstat 函数"
  - "_fstati64 函数"
  - "fstat32i64 函数"
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取有关打开的文件的信息。  
  
## 语法  
  
```  
int _fstat(   
   int fd,  
   struct _stat *buffer   
);  
int _fstat32(   
   int fd,  
   struct __stat32 *buffer   
);  
int _fstat64(   
   int fd,  
   struct __stat64 *buffer   
);  
int _fstati64(   
   int fd,  
   struct _stati64 *buffer   
);  
int _fstat32i64(   
   int fd,  
   struct _stat32i64 *buffer   
);  
int _fstat64i32(   
   int fd,  
   struct _stat64i32 *buffer   
);  
```  
  
#### 参数  
 `fd`  
 打开文件的文件描述符。  
  
 `buffer`  
 指向要存储结果的结构的指针。  
  
## 返回值  
 如果获取文件状态信息，则返回 0。 返回值 –1 指示错误。 如果文件说明符无效或 `buffer` 是 `NULL`, ，则调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则 `errno` 设置为 `EBADF`, 、 对于无效的文件说明符，或为 `EINVAL`, ，如果 `buffer` 是 `NULL`。  
  
## 备注  
 `_fstat` 函数可获取有关关联的打开文件的信息 `fd` 并将其存储在由指向结构 `buffer`。`_stat` SYS\\Stat.h、 中定义的结构包含以下字段。  
  
 `st_atime`  
 最后一个文件访问时间。  
  
 `st_ctime`  
 创建文件的时间。  
  
 `st_dev`  
 如果某一设备， `fd`; 否则为 0。  
  
 `st_mode`  
 文件模式信息的位掩码。`_S_IFCHR` 如果位将设置 `fd` 指的是一种设备。`_S_IFREG` 如果位将设置 `fd` 指的是一个普通的文件。 读\/写位将设置根据文件的权限模式。`_S_IFCHR` 和 SYS\\Stat.h 中定义了其他常量。  
  
 `st_mtime`  
 文件的上次修改时间。  
  
 `st_nlink`  
 在非 NTFS 文件系统上始终为 1。  
  
 `st_rdev`  
 如果某一设备， `fd`; 否则为 0。  
  
 `st_size`  
 以字节为单位的文件的大小。  
  
 如果 `fd` 指的是一种设备， `st_atime`, ，`st_ctime`, ，`st_mtime`, ，和 `st_size` 字段不是有意义。  
  
 因为 Stat.h 使用 [\_dev\_t](../../c-runtime-library/standard-types.md) 键入，Types.h 中定义，则必须在代码中包括 Types.h Stat.h 之前。  
  
 `_fstat64`, 它使用 `__stat64` 结构，请允许文件创建日期来向上表示通过 23:59:59，3000 年 12 月 31 日，UTC; 而其他函数只表示 23:59:59 2038 年 1 月 18 日，UTC 日期。 午夜 1970 年 1 月 1 日，是所有这些函数的日期范围的下限。  
  
 这些函数的变体支持 32 位或 64 位时间类型和 32 位或 64 位文件长度。 第一个数字后缀（`32` 或 `64`）表示所用时间类型的大小；第二个后缀是 `i32` 或 `i64`，表示以 32 位还是 64 位整数表示文件大小。  
  
 `_fstat` 等效于 `_fstat64i32`, ，和 `struct``_stat` 包含 64 位时间。 也是如此除非 `_USE_32BIT_TIME_T` 定义，这种情况下这一旧行为中有效，则是 `_fstat` 使用 32 位时而和 `struct``_stat` 包含 32 位时间。 同样适用于 `_fstati64`。  
  
### \_stat 时间类型和文件长度类型变体  
  
|函数|已定义 \_USE\_32BIT\_TIME\_T？|时间类型|文件长度类型|  
|--------|--------------------------------|----------|------------|  
|`_fstat`|未定义|64 位|32 位|  
|`_fstat`|已定义|32 位|32 位|  
|`_fstat32`|不受宏定义影响|32 位|32 位|  
|`_fstat64`|不受宏定义影响|64 位|64 位|  
|`_fstati64`|未定义|64 位|64 位|  
|`_fstati64`|已定义|32 位|64 位|  
|`_fstat32i64`|不受宏定义影响|32 位|64 位|  
|`_fstat64i32`|不受宏定义影响|64 位|32 位|  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`_fstat`|\<.h \> 和 \< sys\/types.h \>|  
|`_fstat32`|\<.h \> 和 \< sys\/types.h \>|  
|`_fstat64`|\<.h \> 和 \< sys\/types.h \>|  
|`_fstati64`|\<.h \> 和 \< sys\/types.h \>|  
|`_fstat32i64`|\<.h \> 和 \< sys\/types.h \>|  
|`_fstat64i32`|\<.h \> 和 \< sys\/types.h \>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fstat.c  
// This program uses _fstat to report  
// the size of a file named F_STAT.OUT.  
  
#include <io.h>  
#include <fcntl.h>  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <errno.h>  
#include <share.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int fd, result;  
   char buffer[] = "A line to output";  
   char timebuf[26];  
   errno_t err;  
  
   _sopen_s( &fd,  
             "f_stat.out",  
             _O_CREAT | _O_WRONLY | _O_TRUNC,  
             _SH_DENYNO,  
             _S_IREAD | _S_IWRITE );  
   if( fd != -1 )  
      _write( fd, buffer, strlen( buffer ) );  
  
   // Get data associated with "fd":   
   result = _fstat( fd, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      if (errno == EBADF)  
        printf( "Bad file descriptor.\n" );  
      else if (errno == EINVAL)  
        printf( "Invalid argument to _fstat.\n" );  
   }  
   else  
   {  
      printf( "File size     : %ld\n", buf.st_size );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid argument to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
   _close( fd );  
}  
```  
  
```Output  
文件大小︰ 16 次修改︰ 星期三 5 月 7 日 15:25:11 2003年  
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_filelength、\_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)