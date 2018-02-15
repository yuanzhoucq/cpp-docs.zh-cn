---
title: "_ftime_s、_ftime32_s、_ftime64_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
dev_langs:
- C++
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baf4371e90dfe06a4896c33937f578a2483475d3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s、_ftime32_s、_ftime64_s
获取当前时间。 这些是具有安全增强功能的 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### <a name="parameters"></a>参数  
 `timeptr`  
 指向`_timeb`， `__timeb32`，或`__timeb64`结构。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回零；如果失败，则返回错误代码。 如果 `timeptr` 为 `NULL`，则返回值为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_ftime_s`函数获取当前本地时间，并将其存储在通过指向的结构`timeptr`。 `_timeb`， `__timeb32`，和`__timeb64`SYS\Timeb.h 中定义结构。 它们包含下表中列出的四个字段。  
  
 `dstflag`  
 如果本地时区目前正在实行夏令时，则为非零。 （请参阅 [_tzset](../../c-runtime-library/reference/tzset.md) 了解有关如何确定夏令时的解释。）  
  
 `millitm`  
 秒的分数（以毫秒为单位）。  
  
 `time`  
 自 1970 年 1 月 1 日午夜 (00: 00:00) 以来的时间（以秒为单位），格式为协调世界时 (UTC)。  
  
 `timezone`  
 从东向西，UTC 与本地时间之间的差值（以分钟为单位）。 根据全局变量 `_timezone` 设置的 `timezone` 值（请参阅 `_tzset`）。  
  
 使用 `__timeb64` 结构的 `_ftime64_s` 允许文件创建日期最大表示为 3000 年 12 月 31 日 23:59:59，UTC；而 `_ftime32_s` 只能表示截至 2038 年 1 月 18 日 23:59:59，UTC 之前的日期。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。  
  
 `_ftime_s` 与 `_ftime64_s` 等效，`_timeb` 包含 64 位时间。 除非定义了 `_USE_32BIT_TIME_T`，这种情况下旧行为有效；`_ftime_s` 使用 32 位时间，`_timeb` 包含 32 位时间。  
  
 `_ftime_s` 会验证其参数。 如果将 null 指针传递为 `timeptr`，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_ftime_s`|\<sys/types.h> 和 \<sys/timeb.h>|  
|`_ftime32_s`|\<sys/types.h> 和 \<sys/timeb.h>|  
|`_ftime64_s`|\<sys/types.h> 和 \<sys/timeb.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_ftime64_s.c  
// This program uses _ftime64_s to obtain the current  
// time and then stores this time in timebuffer.  
  
#include <stdio.h>  
#include <sys/timeb.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _timeb timebuffer;  
   char timeline[26];  
   errno_t err;  
   time_t time1;  
   unsigned short millitm1;  
   short timezone1;  
   short dstflag1;  
  
   _ftime64_s( &timebuffer );  
  
    time1 = timebuffer.time;  
    millitm1 = timebuffer.millitm;  
    timezone1 = timebuffer.timezone;  
    dstflag1 = timebuffer.dstflag;  
  
   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",   
   time1);  
   printf( "Milliseconds: %d\n", millitm1);  
   printf( "Minutes between UTC and local time: %d\n", timezone1);  
   printf( "Daylight savings time flag (1 means Daylight time is in "  
           "effect): %d\n", dstflag1);   
  
   err = ctime_s( timeline, 26, & ( timebuffer.time ) );  
   if (err)  
   {  
       printf("Invalid argument to ctime_s. ");  
   }  
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,  
           &timeline[20] );  
}  
```  
  
```Output  
Seconds since midnight, January 1, 1970 (UTC): 1051553334  
Milliseconds: 230  
Minutes between UTC and local time: 480  
Daylight savings time flag (1 means Daylight time is in effect): 1  
The time is Mon Apr 28 11:08:54.230 2003  
```  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)