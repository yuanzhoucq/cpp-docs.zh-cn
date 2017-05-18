---
title: "localtime_s、_localtime32_s、_localtime64_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs:
- C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: e068c6711630976a2d8b3baea01010bc5e34ed6e
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s
转换时间值并更正本地时区。 这些是具有安全增强功能的 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### <a name="parameters"></a>参数  
 `_tm`  
 指向要填充的时间结构的指针。  
  
 `time`  
 指向存储时间的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码是在 Errno.h 中定义。 有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>错误条件  
  
|`_tm`|`time`|返回值|`_tm` 中的值|调用无效参数处理程序|  
|-----------|------------|------------------|--------------------|---------------------------------------|  
|`NULL`|任何|`EINVAL`|未修改|是|  
|非 `NULL`（指向有效内存）|`NULL`|`EINVAL`|所有字段都设置为 -1|是|  
|非 `NULL`（指向有效内存）|小于 0 或大于 `_MAX__TIME64_T`|`EINVAL`|所有字段都设置为 -1|No|  
  
 对于前两种错误条件，都会调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_localtime32_s` 函数将转换存储为 [time_t](../../c-runtime-library/standard-types.md) 值的时间并将结果存储在 `tm` 类型的结构中。 `long` 值 `timer` 表示自 1970 年 1 月 1 日午夜 (00: 00:00) (UTC) 起经过的秒数. 此值通常从 `time` 函数中获取。  
  
 如果用户首次设置全局环境变量 `TZ`，`_localtime32_s` 将更正本地时区。 设置 `TZ` 时，其他三个环境变量（`_timezone`、`_daylight` 和 `_tzname`）也会自动设置。 如果未设置 `TZ` 变量，`localtime32_s` 将尝试使用控制面板的日期/时间应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md)。 `TZ` 是 Microsoft 扩展名，但并不是 `localtime` 的 ANSI 标准定义的一部分。  
  
> [!NOTE]
>  目标环境应尝试确定夏令时是否生效。  
  
 使用 `__time64_t` 结构的 `_localtime64_s` 允许日期最大值表示为 3001 年 1 月 18 日 23:59:59，协调世界时 (UTC)；而 `_localtime32_s` 能表示截至 2038 年 1 月 18 日 23:59:59 之前的日期，UTC。  
  
 `localtime_s` 是计算出 `_localtime64_s` 的内联函数，且 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 执行此操作将导致 `localtime_s` 计算出 `_localtime32_s`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许此操作。  
  
 结构类型 [tm](../../c-runtime-library/standard-types.md) 的字段存储以下值，其中每个值为 `int`。  
  
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
 如果夏令时生效，则为正值；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负值。 如果设置 `TZ` 环境变量，C 运行时库假设规则适用于美国，以使用该规则实现夏令时 (DST) 的计算。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`localtime_s`|\<time.h>|  
|`_localtime32_s`|\<time.h>|  
|`_localtime64_s`|\<time.h>|  
  
 有关更多兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## <a name="see-also"></a>另请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)

