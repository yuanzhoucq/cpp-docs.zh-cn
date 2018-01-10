---
title: "_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
dev_langs: C++
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2993016e9c6b3a4ea7d47ba8071fab1267e483f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
获取有关打开文件的信息。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `fd`  
 打开文件的文件描述符。  
  
 `buffer`  
 指向存储结果的结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果获取到文件状态信息，则返回 0。 返回值-1 指示错误。 如果文件描述符无效或 `buffer` 是 `NULL`，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，在出现无效文件描述符的情况下，则将 `errno` 设置为 `EBADF`，或者如果 `buffer` 是 `NULL`，则设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_fstat` 函数可获取有关与 `fd` 关联的打开文件的信息，并将其存储在 `buffer` 指向的结构中。 SYS\Stat.h 中定义的 `_stat` 结构包含下列字段。  
  
 `st_atime`  
 上次文件访问的时间。  
  
 `st_ctime`  
 文件的创建时间。  
  
 `st_dev`  
 如果是设备，则为 `fd`；否则为 0。  
  
 `st_mode`  
 文件模式信息的位掩码。 如果 `fd` 指的是设备，则设置 `_S_IFCHR` 位。 如果 `fd` 指的是普通文件，则设置 `_S_IFREG` 位。 将根据文件的权限模式设置读/写位。 在 SYS\Stat.h 中定义 `_S_IFCHR` 和其他常量。  
  
 `st_mtime`  
 上次进行文件修改的时间。  
  
 `st_nlink`  
 在非 NTFS 文件系统上始终为 1。  
  
 `st_rdev`  
 如果是设备，则为 `fd`；否则为 0。  
  
 `st_size`  
 文件的大小（以字节为单位）。  
  
 如果 `fd` 指的是设备，`st_atime`、`st_ctime`、`st_mtime` 和 `st_size` 字段无意义。  
  
 因为 Stat.h 使用 Types.h 中定义的 [_dev_t](../../c-runtime-library/standard-types.md) 类型，所以必须在代码中的 Stat.h 之前包含 Types.h。  
  
 使用 `__stat64` 结构的 `_fstat64` 允许文件创建日期最大表示为 3000 年 12 月 31 日 23:59:59，UTC；而其他函数只能表示截至 2038 年 1 月 18 日 23:59:59，UTC 之前的日期。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。  
  
 这些函数的变体支持 32 位或 64 位时间类型以及 32 位或 64 位文件长度。 第一个数字后缀（`32` 或 `64`）表示所用时间类型的大小；第二个后缀是 `i32` 或 `i64`，表示以 32 位还是 64 位整数表示文件大小。  
  
 `_fstat` 与 `_fstat64i32` 等效，`struct _stat` 包含 64 位时间。 除非定义了 `_USE_32BIT_TIME_T`，这种情况下旧行为有效；`_fstat` 使用 32 位时间，`struct _stat` 包含 32 位时间。 这一点也适用于 `_fstati64`。  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat 时间类型和文件长度类型变体  
  
|函数|已定义 _USE_32BIT_TIME_T？|时间类型|文件长度类型|  
|---------------|------------------------------------|---------------|----------------------|  
|`_fstat`|未定义|64 位|32 位|  
|`_fstat`|已定义|32 位|32 位|  
|`_fstat32`|不受宏定义影响|32 位|32 位|  
|`_fstat64`|不受宏定义影响|64 位|64 位|  
|`_fstati64`|未定义|64 位|64 位|  
|`_fstati64`|已定义|32 位|64 位|  
|`_fstat32i64`|不受宏定义影响|32 位|64 位|  
|`_fstat64i32`|不受宏定义影响|64 位|32 位|  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fstat`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat32`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat64`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstati64`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat32i64`|\<sys/stat.h> 和 \<sys/types.h>|  
|`_fstat64i32`|\<sys/stat.h> 和 \<sys/types.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
File size     : 16  
Time modified : Wed May 07 15:25:11 2003  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_access、_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_filelength、_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [_stat、_wstat 函数](../../c-runtime-library/reference/stat-functions.md)