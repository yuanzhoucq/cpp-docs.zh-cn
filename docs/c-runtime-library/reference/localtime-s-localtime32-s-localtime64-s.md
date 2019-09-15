---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 07/09/2019
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: c00a5d23441612d0e70bfafd571bcb25250edb09
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953327"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

将**time_t**的时间值转换为**tm**结构，并更正本地时区。 这些是具有安全增强功能的 [localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>参数

*tmDest*<br/>
指向要填充的时间结构的指针。

*sourceTime*<br/>
指向存储时间的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码是在 Errno.h 中定义。 有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*tmDest*|*sourceTime*|返回值|*TmDest*中的值|调用无效参数处理程序|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|任何|**EINVAL**|未修改|是|
|Not **NULL** （指向有效内存）|**NULL**|**EINVAL**|所有字段都设置为 -1|是|
|Not **NULL** （指向有效内存）|小于0或大于 **_MAX__TIME64_T**|**EINVAL**|所有字段都设置为 -1|No|

对于前两种错误条件，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则这些函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**Localtime_s**函数将存储的时间转换为[time_t](../../c-runtime-library/standard-types.md)值，并将结果存储在[tm](../../c-runtime-library/standard-types.md)类型的结构中。 **Time_t**值*sourceTime*表示自00:00:00 年1月 1970 1 日午夜（）起经过的秒数。 此值通常是从[time](time-time32-time64.md)函数获取的。

如果用户首先设置全局环境变量**TZ**，则**localtime_s**会纠正本地时区。 设置为**TZ**时，还会自动设置其他三个环境变量（ **_timezone**、 **_daylight**和 **_tzname**）。 如果未设置**TZ**变量， **localtime_s**将尝试使用 "控制面板" 的 "日期/时间" 应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](tzset.md)。 **TZ**是 Microsoft 扩展，而不是**localtime**的 ANSI 标准定义的一部分。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。

使用 **__time64_t**结构的 **_localtime64_s**允许日期向上表示为23:59:59 年1月 3001 18 日，协调世界时（UTC），而 **_Localtime32_s**表示从年1月18日到23:59:59 的日期2038，UTC。

**localtime_s**是一个计算结果为 **_localtime64_s**的内联函数，而**time_t**等效于 **__time64_t**。 如果需要强制编译器将**time_t**解释为旧的32位**time_t**，可定义 **_USE_32BIT_TIME_T**。 这样做会导致**localtime_s**计算为 **_localtime32_s**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

结构类型[tm](../../c-runtime-library/standard-types.md)的字段存储以下值，其中每个值都是**int**。

|字段|描述|
|-|-|
|**tm_sec**|每分钟的秒数（0-59）。|
|**tm_min**|每小时后的分钟数（0-59）。|
|**tm_hour**|午夜（0-23）。|
|**tm_mday**|每月的某一日（1-31）。|
|**tm_mon**|Month （0-11;1月 = 0）。|
|**tm_year**|年（当前年份减去 1900）。|
|**tm_wday**|一周中的某一日（0-6;星期日 = 0）。|
|**tm_yday**|一年的某一日（0-365;1月1日 = 0）。|
|**tm_isdst**|如果夏令时生效，则为正值；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负值。|

如果设置了**TZ**环境变量，C 运行时库将假定与用于实现夏令时（DST）的计算的美国适用的规则。

## <a name="requirements"></a>要求

|例程所返回的值|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**localtime_s**、 **_localtime32_s**、 **_localtime64_s**|\<time.h>|\<ctime > 或\<time .h >|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

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
        newtime.tm_hour -= 12;        // to 12-hour clock.
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

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
