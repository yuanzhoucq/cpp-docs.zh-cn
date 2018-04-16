---
title: "asctime、_wasctime | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
dev_langs:
- C++
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c89b43613e1eb82eb35876ea733e13c5d2995352
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="asctime-wasctime"></a>asctime、_wasctime
将 `tm` 时间结构转换为字符串。 提供这些函数的更多安全版本；请参阅 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *asctime(   
   const struct tm *timeptr   
);  
wchar_t *_wasctime(   
   const struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>参数  
 `timeptr`  
 时间/日期结构。  
  
## <a name="return-value"></a>返回值  
 `asctime` 返回一个指向字符串结果的指针；`_wasctime` 返回一个指向宽字符串结果的指针。 无错误返回值。  
  
## <a name="remarks"></a>备注  
 提供这些函数的更多安全版本；请参阅 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
 `asctime` 函数将存储为结构的时间转换为字符串。 通常情况下，`timeptr` 值通过调用 `gmtime` 或 `localtime` 获取，这两个函数均返回一个指向 TIME_H 中定义的 `tm` 结构的指针。  
  
|timeptr 成员|值|  
|--------------------|-----------|  
|`tm_hour`|小时，自午夜 (0-23)|  
|`tm_isdst`|如果夏令时生效，则为正；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。|  
|`tm_mday`|月 (1-31) 天|  
|`tm_min`|分钟后小时 (0-59)|  
|`tm_mon`|月 (0-11;年 1 月 = 0）|  
|`tm_sec`|分钟 (0-59) 之后的秒|  
|`tm_wday`|周的天 (0-6;星期日 = 0）|  
|`tm_yday`|年份 (0-365; 天1 月 1 日 = 0)|  
|`tm_year`|年（当前年份减去 1900）|  
  
 转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 [time](../../c-runtime-library/reference/time-time32-time64.md)、[_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函数，有关定义时区环境和全局变量的信息，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md)。  
  
 `asctime` 生成的字符串结果正好包含 26 个字符，格式为 `Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小时制。 所有字段都具有固定宽度。 换行符和空字符占据字符串的最后两个位置。 `asctime` 使用单个静态分配的缓冲区来保存返回的字符串。 每次调用此函数都会破坏上一次调用的结果。  
  
 `_wasctime` 是 `asctime` 的宽字符版本。 除此以外，`_wasctime` 和 `asctime` 的行为完全相同。  
  
 这些函数验证其参数。 如果 `timeptr` 是空指针或包含超出范围的值，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回 `NULL`，并且将 `errno` 设置为 `EINVAL`。  
  
### <a name="generic-text-routine-mapping"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime`|`asctime`|`asctime`|`_wasctime`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`asctime`|\<time.h>|  
|`_wasctime`|\<time.h> 或 \<wchar.h>|  
  
## <a name="example"></a>示例  
 此程序以长整型 `aclock` 格式进行系统时间设置，将其转换为 `newtime` 结构，然后使用 `asctime` 函数将其转换为字符串形式以进行输出。  
  
```  
// crt_asctime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
    struct tm   *newTime;  
    time_t      szClock;  
  
    // Get time in seconds  
    time( &szClock );  
  
    // Convert time to struct tm form   
    newTime = localtime( &szClock );  
  
    // Print local time as a string.  
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996  
    // Note: asctime is deprecated; consider using asctime_s instead  
}  
```  
  
```Output  
Current date and time: Sun Feb 03 11:38:58 2002  
```  
  
## <a name="see-also"></a>请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)