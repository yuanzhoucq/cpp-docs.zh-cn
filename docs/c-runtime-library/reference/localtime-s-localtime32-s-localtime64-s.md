---
title: localtime_s、_localtime32_s、_localtime64_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1125f9a66a471b664e42ddbd5164611a4cb2ae69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s

将转换**time_t**时间值到**tm**结构，并更正为本地时区。 这些是具有安全增强功能的 [localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t localtime_s(
   struct tm* tmDest,
   const time_t *sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   const time32_t *sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   const _time64_t *sourceTime
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

|*tmDest*|*sourceTime*|返回值|中的值*tmDest*|调用无效参数处理程序|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|任何|**EINVAL**|未修改|是|
|不**NULL** （指向有效的内存）|**NULL**|**EINVAL**|所有字段都设置为 -1|是|
|不**NULL** （指向有效的内存）|小于 0 或大于 **_MAX__TIME64_T**|**EINVAL**|所有字段都设置为 -1|否|

对于前两种错误条件，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**_Localtime32_s**函数将存储为时间为[time_t](../../c-runtime-library/standard-types.md)值并将结果存储在类型的结构[tm](../../c-runtime-library/standard-types.md)。 **长**值*sourceTime*表示自午夜以来经过的秒 (00: 00:00)、 1970 年 1 月 1 日，UTC。 此值通常从获取[时间](time-time32-time64.md)函数。

**_localtime32_s**更正为本地时区，如果用户先设置全局环境变量**TZ**。 当**TZ**设置，其他三个环境变量 (**_timezone**， **_daylight**，和 **_tzname**) 以及自动设置。 如果**TZ**未设置变量， **localtime32_s**尝试使用控制面板中的日期/时间应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](tzset.md)。 **TZ**是 Microsoft 扩展和不属于的 ANSI 标准定义**localtime**。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。

**_localtime64_s**，它使用 **__time64_t**结构，而允许的日期以通过 23:59:59，年 1 月 18 日，3001，协调世界时 (UTC) 表示向上 **_localtime32_s**表示到 23:59:59 2038 年 1 月 18 日，UTC 日期。

**localtime_s**是内联函数计算结果为 **_localtime64_s**，和**time_t**等效于 **__time64_t**。 如果需要强制编译器将解释**time_t**为旧的 32 位**time_t**，你可以定义 **_USE_32BIT_TIME_T**。 这将导致这样做**localtime_s**计算结果为 **_localtime32_s**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

结构类型的字段[tm](../../c-runtime-library/standard-types.md)存储下面的值，其中每个**int**。

|字段|描述|
|-|-|
|**tm_sec**|分钟之后的秒 (0-59)。|
|**tm_min**|分钟后小时 (0-59)。|
|**tm_hour**|小时，自午夜 (0-23)。|
|**tm_mday**|某一天的月份 (1-31)。|
|**tm_mon**|月 (0-11;年 1 月 = 0）。|
|**tm_year**|年（当前年份减去 1900）。|
|**tm_wday**|星期几 (0-6;星期日 = 0）。|
|**tm_yday**|年的某一天 (0-365;1 月 1 日 = 0)。|
|**tm_isdst**|如果夏令时生效，则为正值；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负值。|

如果**TZ**设置环境变量，则 C 运行时库假定规则适用于美国境内用于实现夏令时 (DST) 的计算。

## <a name="requirements"></a>要求

|例程|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**localtime_s**， **_localtime32_s**， **_localtime64_s**|\<time.h>|\<ctime > 或\<.h >|

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
