---
title: "_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
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
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
dev_langs: C++
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18cfdda310149c18ef8983b10afb5c901b256510
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat、_stat32、_stat64、_stati64、_stat32i64、_stat64i32、_wstat、_wstat32、_wstat64、_wstati64、_wstat32i64、_wstat64i32
获取文件状态信息。  
  
## <a name="syntax"></a>语法  
  
```  
int _stat(  
   const char *path,  
   struct _stat *buffer   
);  
int _stat32(  
   const char *path,  
   struct __stat32 *buffer   
);  
int _stat64(  
   const char *path,  
   struct __stat64 *buffer   
);  
int _stati64(  
   const char *path,  
   struct _stati64 *buffer   
);  
int _stat32i64(  
   const char *path,  
   struct _stat32i64 *buffer   
);  
int _stat64i32(  
   const char *path,  
   struct _stat64i32 *buffer   
);  
int _wstat(  
   const wchar_t *path,  
   struct _stat *buffer   
);  
int _wstat32(  
   const wchar_t *path,  
   struct __stat32 *buffer   
);  
int _wstat64(  
   const wchar_t *path,  
   struct __stat64 *buffer   
);  
int _wstati64(  
   const wchar_t *path,  
   struct _stati64 *buffer   
);  
int _wstat32i64(  
   const wchar_t *path,  
   struct _stat32i64 *buffer   
);  
int _wstat64i32(  
   const wchar_t *path,  
   struct _stat64i32 *buffer   
);  
```  
  
#### <a name="parameters"></a>参数  
 `path`  
 指向字符串的指针，该字符串包含现有文件或目录的路径。  
  
 `buffer`  
 指向存储结果的结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果获取到文件状态信息，则这些函数将返回 0。 返回值-1 指示错误，在这种情况下`errno`设置为`ENOENT`，，该值指示，该文件名或路径未找到。 返回值为 `EINVAL` 表示参数无效；这种情况下 `errno` 还会设置为 `EINVAL` 。  
  
 关于此代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果文件上的日期戳晚于 1970 年 1 月 1 日午夜，且早于 3000 年 12 月 31 日 23:59:59 (UTC)，就可以表示该日期戳，除非使用 `_stat32` 或 `_wstat32`，或已定义 `_USE_32BIT_TIME_T`，在这种情况下只能表示 2038 年 1 月 18 日 23:59:59 (UTC) 之前的日期。  
  
## <a name="remarks"></a>备注  
 `_stat` 函数可获取有关 `path` 指定的文件或目录的信息，并将其存储在 `buffer`指向的结构中。 `_stat` 将根据情况自动处理多字节字符串参数，根据当前正在使用的多字节代码页识别多字节字符序列。  
  
 `_wstat` 是 `_stat`的宽字符版本； `path` 的 `_wstat` 参数是宽字符字符串。 `_wstat` 和 `_stat` 的行为方式相同，只不过 `_wstat` 不处理多字节字符字符串。  
  
 这些函数的变体支持 32 位或 64 位时间类型以及 32 位或 64 位文件长度。 第一个数字后缀（`32` 或 `64`）表示所用时间类型的大小；第二个后缀是 `i32` 或 `i64`，表示以 32 位还是 64 位整数表示文件大小。  
  
 `_stat` 与 `_stat64i32`等效， `struct _stat` 包含 64 位时间。 除非定义了 `_USE_32BIT_TIME_T` ，这种情况下旧行为有效； `_stat` 使用 32 位时间， `struct _stat` 包含 32 位时间。 这一点也适用于 `_stati64`。  
  
> [!NOTE]
>  `_wstat` 不适用于 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 符号链接。 在这些情况下， `_wstat` 将始终报告文件大小为 0。 `_stat` 适用于符号链接。  
  
 此函数验证其参数。 如果 `path` 或 `buffer` 是 `NULL`，则会调用无效参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)指向的结构中。  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat 时间类型和文件长度类型变体  
  
|函数|已定义 _USE_32BIT_TIME_T？|时间类型|文件长度类型|  
|---------------|------------------------------------|---------------|----------------------|  
|`_stat`, `_wstat`|未定义|64 位|32 位|  
|`_stat`, `_wstat`|已定义|32 位|32 位|  
|`_stat32`, `_wstat32`|不受宏定义影响|32 位|32 位|  
|`_stat64`, `_wstat64`|不受宏定义影响|64 位|64 位|  
|`_stati64`, `_wstati64`|未定义|64 位|64 位|  
|`_stati64`, `_wstati64`|已定义|32 位|64 位|  
|`_stat32i64`, `_wstat32i64`|不受宏定义影响|32 位|64 位|  
|`_stat64i32`, `_wstat64i32`|不受宏定义影响|64 位|32 位|  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstat`|`_stat`|`_stat`|`_wstat`|  
|`_tstat64`|`_stat64`|`_stat64`|`_wstat64`|  
|`_tstati64`|`_stati64`|`_stati64`|`_wstati64`|  
|`_tstat32i64`|`_stat32i64`|`_stat32i64`|`_wstat32i64`|  
|`_tstat64i32`|`_stat64i32`|`_stat64i32`|`_wstat64i32`|  
  
 SYS\STAT.H 中定义的 `_stat` 结构包含下列字段。  
  
 `st_gid`  
 拥有此文件的组的数字标识符（针对 UNIX）。在 Windows 系统上此字段始终为 0。 重定向的文件分类为 Windows 文件。  
  
 `st_atime`  
 上次访问文件的时间。 在 NTFS 上有效，但在 FAT 格式的磁盘驱动器上无效。  
  
 `st_ctime`  
 文件的创建时间。 在 NTFS 上有效，但在 FAT 格式的磁盘驱动器上无效。  
  
 `st_dev`  
 包含文件的磁盘的驱动器号（与 `st_rdev`相同）。  
  
 `st_ino`  
 文件的信息节点号 ( `inode`)（针对 UNIX）。 在 UNIX 文件系统上， `inode` 描述文件日期和时间戳、权限和内容。 当文件硬链接到另一文件时，它们共享同一个 `inode`。 `inode`和 `st_ino`在 FAT、HPFS 或 NTFS 文件系统中没有任何意义。  
  
 `st_mode`  
 文件模式信息的位掩码。 如果 `_S_IFDIR` 指定目录，会设置 `path` 位；如果 `_S_IFREG` 指定一个普通文件或设备，会设置 `path` 位。 根据文件的权限模式设置用户读/写位；根据文件扩展名设置用户执行位。  
  
 `st_mtime`  
 上次修改文件的时间。  
  
 `st_nlink`  
 在非 NTFS 文件系统上始终为 1。  
  
 `st_rdev`  
 包含文件的磁盘的驱动器号（与 `st_dev`相同）。  
  
 `st_size`  
 文件大小，以字节为单位；带有 `i64` 后缀**的变体为 64 位整数。**  
  
 `st_uid`  
 拥有文件的用户的数字标识符（针对 UNIX）。 此字段在 Windows 系统上始终为 0。 重定向的文件分类为 Windows 文件。  
  
 如果 `path` 指的是一种设备，则 `st_size`、各种时间字段、 `st_dev`和 `st_rdev` 结构中的 `_stat` 字段没有意义。 因为 STAT.H 使用 TYPES.H 中定义的 [_dev_t](../../c-runtime-library/standard-types.md) 类型，所以必须在代码中的 STAT.H 前面包含 TYPES.H。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|----------------------|  
|`_stat`, `_stat32`, `_stat64`, `_stati64`, `_stat32i64`, `_stat64i32`|\<sys/types.h> 后跟 \<sys/stat.h>|\<errno.h>|  
|`_wstat`, `_wstat32`, `_wstat64`, `_wstati64`, `_wstat32i64`, `_wstat64i32`|\<sys/types.h> 后跟 \<sys/stat.h> 或 \<wchar.h>|\<errno.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_stat.c  
// This program uses the _stat function to  
// report information about the file named crt_stat.c.  
  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int result;  
   char timebuf[26];  
   char* filename = "crt_stat.c";  
   errno_t err;  
  
   // Get data associated with "crt_stat.c":   
   result = _stat( filename, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      perror( "Problem getting information" );  
      switch (errno)  
      {  
         case ENOENT:  
           printf("File %s not found.\n", filename);  
           break;  
         case EINVAL:  
           printf("Invalid parameter to _stat.\n");  
           break;  
         default:  
           /* Should never be reached. */  
           printf("Unexpected error in _stat.\n");  
      }  
   }  
   else  
   {  
      // Output some of the statistics:   
      printf( "File size     : %ld\n", buf.st_size );  
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid arguments to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
}  
```  
  
```Output  
File size     : 732  
Drive         : C:  
Time modified : Thu Feb 07 14:39:36 2002  
```  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_access、_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)