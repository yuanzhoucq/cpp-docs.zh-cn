---
title: "_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
dev_langs: C++
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 08e3cd90e4c86365694c098973f45d667621ea98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
设置文件修改时间。  
  
## <a name="syntax"></a>语法  
  
```  
int _utime(  
   const char *filename,  
   struct _utimbuf *times   
);  
int _utime32(  
   const char *filename,  
   struct __utimbuf32 *times   
);  
int _utime64(  
   const char *filename,  
   struct __utimbuf64 *times   
);  
int _wutime(  
   const wchar_t *filename,  
   struct _utimbuf *times   
);  
int _wutime32(  
   const wchar_t *filename,  
   struct __utimbuf32 *times   
);  
int _wutime64(  
   const wchar_t *filename,  
   struct __utimbuf64 *times   
);  
```  
  
#### <a name="parameters"></a>参数  
 `filename`  
 指向包含路径或文件名的字符串的指针。  
  
 `times`  
 指向存储时间值的指针。  
  
## <a name="return-value"></a>返回值  
 如果更改了文件修改时间，则这些函数均将返回 0。 返回值-1 指示错误。 如果传递的参数无效，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 -1 并将 `errno` 设置为以下值之一：  
  
 `EACCES`  
 路径指定目录或只读文件  
  
 `EINVAL`  
 无效的 `times` 参数  
  
 `EMFILE`  
 打开的文件太多（必须打开文件以更改其修改时间）  
  
 `ENOENT`  
 找不到路径或文件名  
  
 有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果更改日期在 1970 年 1 月 1 日午夜之后且在所使用的函数的结束日期之前，则可以更改文件的日期。 `_utime` 和 `_wutime` 使用 64 位时间值，因此结束日期为协调世界时 3000 年 12 月 31 日 23:59:59。 如果将 `_USE_32BIT_TIME_T` 定义为强制执行旧的行为，则结束日期为协调世界时 2038 年 1 月 18 日 23:59:59。 `_utime32` 或 `_wutime32` 使用 32 位时间类型，无论是否定义了 `_USE_32BIT_TIME_T`，且始终使用较早的结束时间。 `_utime64` 或 `_wutime64` 始终使用 64 位时间类型，因此这些函数始终支持较晚的结束日期。  
  
## <a name="remarks"></a>备注  
 `_utime` 函数设置 `filename` 指定的文件修改时间*。* 进程必须拥有文件的写入权限才能更改时间。 在 Windows 操作系统中，可以在 `_utimbuf` 结构中更改访问时间和修改时间。 如果 `times` 是 `NULL` 指针，则将修改时间设置为当前的本地时间。 否则，`times` 必须指向 SYS\UTIME.H 中定义的某个结构或类型 `_utimbuf`。  
  
 `_utimbuf` 结构存储 `_utime` 更改文件修改日期所使用的文件访问时间和修改时间。 此结构包含以下字段，其均为类型 `time_t`：  
  
 `actime`  
 文件访问时间  
  
 `modtime`  
 文件修改时间  
  
 `_utimbuf` 结构（`_utimebuf32` 和 `__utimbuf64`）的特定版本使用 32 位和 64 位版本的时间类型定义。 这些是此函数的 32 位和 64 位特定版本中使用的内容。 `_utimbuf` 自身默认使用 64 位时间类型，除非定义了 `_USE_32BIT_TIME_T`。  
  
 `_utime` 等同于 `_futime`，只不过 `_utime` 的 `filename` 参数是文件名或文件的路径名称，而不是打开的文件的文件描述符。  
  
 `_wutime` 是 `_utime` 的宽字符版本；`filename` 的 `_wutime` 参数是宽字符字符串。 否则这些函数具有相同行为。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需标头|可选标头|  
|-------------|----------------------|----------------------|  
|`_utime`, `_utime32`, `_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_wutime`|\<utime.h> 或 \<wchar.h>|\<errno.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 此程序使用 `_utime` 将文件修改时间设置为当前时间。  
  
```  
// crt_utime.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/utime.h>  
#include <time.h>  
  
int main( void )  
{  
   struct tm tma = {0}, tmm = {0};  
   struct _utimbuf ut;  
  
   // Fill out the accessed time structure  
   tma.tm_hour = 12;  
   tma.tm_isdst = 0;  
   tma.tm_mday = 15;  
   tma.tm_min = 0;  
   tma.tm_mon = 0;  
   tma.tm_sec = 0;  
   tma.tm_year = 103;  
  
   // Fill out the modified time structure  
   tmm.tm_hour = 12;  
   tmm.tm_isdst = 0;  
   tmm.tm_mday = 15;  
   tmm.tm_min = 0;  
   tmm.tm_mon = 0;  
   tmm.tm_sec = 0;  
   tmm.tm_year = 102;  
  
   // Convert tm to time_t  
   ut.actime = mktime(&tma);  
   ut.modtime = mktime(&tmm);  
  
   // Show file time before and after  
   system( "dir crt_utime.c" );  
   if( _utime( "crt_utime.c", &ut ) == -1 )  
      perror( "_utime failed\n" );  
   else  
      printf( "File time modified\n" );  
   system( "dir crt_utime.c" );  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/09/2003  05:38 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
File time modified  
 Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/15/2002  12:00 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
```  
  
## <a name="see-also"></a>另请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [_futime、_futime32、_futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_stat、_wstat 函数](../../c-runtime-library/reference/stat-functions.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)