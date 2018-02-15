---
title: "localtime、_localtime32、_localtime64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
dev_langs:
- C++
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fa4d1b9c0f33df5f172500195edd4f50321d4e5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="localtime-localtime32-localtime64"></a>localtime、_localtime32、_localtime64
转换时间值并更正本地时区。 这些函数的更安全版本已经可用；请参阅 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
struct tm *localtime(  
   const time_t *timer   
);  
struct tm *_localtime32(  
   const __time32_t *timer  
);  
struct tm *_localtime64(  
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>参数  
 `timer`  
 指向存储时间的指针。  
  
## <a name="return-value"></a>返回值  
 如果传递给函数的日期如下所示，则返回一个指向结构结果的指针或 `NULL`：  
  
-   1970 年 1 月 1 日午夜前。  
  
-   2038 年 1 月 19 日 03:14:07 之后（UTC）（使用 `_time32` 和 `time32_t`）。  
  
-   3000 年 12 月 31 日 23:59:59 之后（UTC）（使用 `_time64` 和 `__time64_t`）。  
  
 使用 `__time64_t` 结构的 `_localtime64` 允许日期最大值表示为 3000 年 12 月 31 日 23:59:59，协调世界时 (UTC)；而 `_localtime32` 能表示截至 2038 年 1 月 18 日 23:59:59 的日期，UTC 。  
  
 `localtime` 是计算出 `_localtime64` 的内联函数，且 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 执行此操作将导致 `localtime` 计算出 `_localtime32`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许此操作。  
  
 结构类型 [tm](../../c-runtime-library/standard-types.md) 的字段存储以下值，其中每个值为 `int`：  
  
 `tm_sec`  
 分钟之后的秒 (0-59)。  
  
 `tm_min`  
 分钟后小时 (0-59)。  
  
 `tm_hour`  
 午夜后经过的小时数 (0-23)。  
  
 `tm_mday`  
 某一天的月份 (1-31)。  
  
 `tm_mon`  
 月 (0-11;年 1 月 = 0）。  
  
 `tm_year`  
 年（当前年份减去 1900）。  
  
 `tm_wday`  
 星期几 (0-6;星期日 = 0）。  
  
 `tm_yday`  
 年的某一天 (0-365;1 月 1 日 = 0)。  
  
 `tm_isdst`  
 如果夏令时生效，则为正值；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负值。 如果设置了 `TZ` 环境变量，C 运行时库会假设规则适用于美国，以使用该规则实现夏令时 (DST) 的计算。  
  
## <a name="remarks"></a>备注  
 `localtime` 函数将转换存储为 [time_t](../../c-runtime-library/standard-types.md) 值的时间并将结果存储在 `tm` 类型的结构中。 `long` 值 `timer` 表示自 1970 年 1 月 1 日午夜 (00: 00:00) (UTC) 起经过的秒数. 此值通常从 `time` 函数中获取。  
  
 `gmtime`、`mktime`、`mkgmtime` 和 `localtime` 的 32 位和 64 位版本均为每个线程使用单个 `tm` 结构以进行转换。 每次调用这些例程都会破坏上一次调用的结果。  
  
 如果用户首次设置全局环境变量 `TZ`，`localtime` 将更正本地时区。 设置 `TZ` 时，其他三个环境变量（`_timezone`、`_daylight` 和 `_tzname`）也会自动设置。 如果未设置 `TZ` 变量，`localtime` 将尝试使用控制面板的日期/时间应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md)。 `TZ` 是 Microsoft 扩展名，但并不是 `localtime` 的 ANSI 标准定义的一部分。  
  
> [!NOTE]
>  目标环境应尝试确定夏令时是否生效。  
  
 这些函数验证其参数。 如果 `timer` 为空指针，或计时器值为负值，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 `NULL`，并将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`localtime`|\<time.h>|  
|`_localtime32`|\<time.h>|  
|`_localtime64`|\<time.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_localtime.cpp  
// compile with: /W3  
/* This program uses _time64 to get the current time   
 * and then uses localtime64() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm *newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
  
        _time64( &long_time );           // Get time as 64-bit integer.  
                                         // Convert to local time.  
        newtime = _localtime64( &long_time ); // C4996  
        // Note: _localtime64 deprecated; consider _localetime64_s  
  
        if( newtime->tm_hour > 12 )        // Set up extension.  
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime->tm_hour > 12 )        // Convert from 24-hour  
                newtime->tm_hour -= 12;    //   to 12-hour clock.  
        if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime->tm_hour = 12;  
  
        char buff[30];  
        asctime_s( buff, sizeof(buff), newtime );  
        printf( "%.19s %s\n", buff, am_pm );  
}  
```  
  
```Output  
Tue Feb 12 10:05:58 AM  
```  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)