---
title: "_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_utime64"
  - "_utime"
  - "_wutime"
  - "_wutime64"
  - "_wutime32"
  - "_utime32"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tutime"
  - "_utime64"
  - "wutime"
  - "utime32"
  - "wutime64"
  - "_utime"
  - "wutime32"
  - "_wutime"
  - "utime"
  - "utime64"
  - "_wutime64"
  - "_utime32"
  - "_tutime64"
  - "_wutime32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tutime 函数"
  - "utime32 函数"
  - "utime64 函数"
  - "_utime 函数"
  - "_tutime32 函数"
  - "时间 [C++], 文件修改"
  - "wutime 函数"
  - "_wutime 函数"
  - "_wutime32 函数"
  - "_tutime64 函数"
  - "_tutime 函数"
  - "文件 [C++], 修改时间"
  - "_wutime64 函数"
  - "_utime32 函数"
  - "utime 函数"
  - "_utime64 函数"
  - "wutime64 函数"
  - "wutime32 函数"
  - "tutime64 函数"
  - "tutime32 函数"
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置文件修改时间。  
  
## 语法  
  
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
  
#### 参数  
 `filename`  
 指向包含的路径或文件名的字符串指针。  
  
 `times`  
 为存储的时间值的指针。  
  
## 返回值  
 如果已更改文件修改时间，其中每个函数返回 0。 返回值 –1 指示错误。 如果传递了无效的参数，则将调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回\-1 和 `errno` 设置为下列值之一︰  
  
 `EACCES`  
 路径指定目录或只读文件  
  
 `EINVAL`  
 无效 `times` 参数  
  
 `EMFILE`  
 （该文件必须打开要更改其修改时间） 的打开文件太多  
  
 `ENOENT`  
 路径或文件名找不到  
  
 请参阅 [\_doserrno、 errno、 \_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 有关这些功能，以及其他详细信息，返回代码。  
  
 如果更改日期为 1970 年 1 月 1 日午夜之后，使用的函数的结束日期之前，可以为文件更改的日期。`_utime` 和 `_wutime` 使用 64 位时间值，因此结束日期是 23:59:59，3000 年 12 月 31 日，UTC。 如果 `_USE_32BIT_TIME_T` 定义若要强制这一旧行为，结束日期为 23:59:59 2038 年 1 月 18 日，UTC。`_utime32` 或 `_wutime32` 使用 32 位时间类型，而不管是否 `_USE_32BIT_TIME_T` 定义，并且始终具有较早的结束日期。`_utime64` 或 `_wutime64` 始终使用 64 位时间类型，因此这些函数始终支持更高版本的结束日期。  
  
## 备注  
 `_utime` 函数将设置指定的文件的修改时间 `filename`*。*若要更改的时间，该进程必须到该文件具有写访问权限。 Windows 操作系统中，您可以更改访问时间和修改时间以 `_utimbuf` 结构。 如果 `times` 是 `NULL` 指针，修改时间设置为当前的本地时间。 否则为 `times` 必须指向类型的结构 `_utimbuf`, 在 SYS\\UTIME 中定义。H。  
  
 `_utimbuf` 结构存储使用的文件访问和修改时间 `_utime` 用于更改文件修改日期。 此结构中有以下字段，它们将这两个类型 `time_t`:  
  
 `actime`  
 文件访问的时间  
  
 `modtime`  
 文件修改时间  
  
 特定版本的 `_utimbuf` 结构 \(`_utimebuf32` 和 `__utimbuf64`\) 使用的时间类型的 32 位和 64 位版本进行定义。 这些凭据用于在 32 位和 64 位特定版本的此函数。`_utimbuf` 默认情况下本身使用 64 位时类型，除非 `_USE_32BIT_TIME_T` 定义。  
  
 `_utime` 等同于 `_futime` 只不过 `filename` 参数 `_utime` 是一个文件名或文件，而不是打开的文件的文件描述符的路径。  
  
 `_wutime` 是 `_utime` 的宽字符版本；`filename` 的 `_wutime` 参数是宽字符字符串。 否则这些函数具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_utime`, `_utime32`, `_utime64`|\< \> sys\/utime.h|\<errno.h\>|  
|`_utime64`|\< \> sys\/utime.h|\<errno.h\>|  
|`_wutime`|\< utime.h \> 或 \< wchar.h \>|\<errno.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 此程序使用 `_utime` 可为当前时间设置的文件修改时间。  
  
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
  
## 示例输出  
  
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
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [\_futime、\_futime32、\_futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)