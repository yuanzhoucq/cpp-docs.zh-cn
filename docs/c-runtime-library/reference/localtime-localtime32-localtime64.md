---
title: localtime、_localtime32、_localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 21496b71c354c7bed7b87526dc40bc9b24865da2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342133"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime、_localtime32、_localtime64

转换时间值并更正本地时区。 这些函数的更安全版本已经可用；请参阅 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)。

## <a name="syntax"></a>语法

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>参数

*源时间*<br/>
指向存储时间的指针。

## <a name="return-value"></a>返回值

返回指向结构结果的指针 **，如果传递给**函数的日期为：

- 1970 年 1 月 1 日午夜前。

- 在 2038 年 1 月 19 日 03：14：07 之后，UTC（使用 **_time32**和**time32_t）。**

- 在 23：59：59， 12 月 31， 3000， UTC （使用 **_time64**和 **__time64_t**） 之后。

**_localtime64**（_localtime64 使用 **__time64_t**结构，允许日期在 2000 年 12 月 31 日 23：59：59（协调通用时间 （UTC） 之前表示，而 **_localtime32**表示日期为 2038 年 1 月 18 日 23：59：59，UTC。

**当地时间**是一个内联函数，它计算为 **_localtime64，time_t**相当于**time_t****__time64_t。** 如果需要强制编译器将**time_t**解释为旧的 32 位**time_t**，则可以定义 **_USE_32BIT_TIME_T**。 这样做将导致**当地时间**评估到 **_localtime32**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

结构类型[tm](../../c-runtime-library/standard-types.md)的字段存储以下值，每个值都是**int**：

|字段|说明|
|-|-|
|**tm_sec**|一分钟后秒 （0 - 59）。|
|**tm_min**|一小时后几分钟 （0 - 59）。|
|**tm_hour**|午夜起（0 - 23日）的营业时间。|
|**tm_mday**|月日（1 - 31）。|
|**tm_mon**|月 （0 - 11;1 月 = 0）。|
|**tm_year**|年（当前年份减去 1900）。|
|**tm_wday**|星期一（0 - 6;周日 = 0）。|
|**tm_yday**|一年中的日子（0 - 365;1 月 1 = 0）。|
|**tm_isdst**|如果夏令时生效，则为正值；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负值。|

如果设置了**TZ**环境变量，C 运行时库将假定适合美国的规则来实现夏令时 （DST） 的计算。

## <a name="remarks"></a>备注

**本地时间**函数转换存储为[time_t](../../c-runtime-library/standard-types.md)值的时间，并将结果存储在[tm](../../c-runtime-library/standard-types.md)类型的结构中。 **长**值*源时间*表示自午夜 （00：00：00） 到 UTC 1970 年 1 月 1 日以来的秒数。 此值通常从[时间](time-time32-time64.md)函数获得。

**tm** gmtime、mktime、mkgmtime 和**本地时间的**32[mktime](mktime-mktime32-mktime64.md)位和[mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)64 位版本都使用每个线程的单个 tm 结构进行转换。 [gmtime](gmtime-gmtime32-gmtime64.md) 每次调用这些例程都会破坏上一次调用的结果。

如果用户首先设置全局环境变量**TZ，** 则本地时区的**本地时间**更正。 设置**TZ**时，还会自动设置另外三个环境变量 **（_timezone、_daylight**和 **_tzname）。** **_daylight** 如果未设置**TZ**变量，**则本地时间**尝试使用控制面板中的日期/时间应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](tzset.md)。 **TZ**是微软的扩展，不是**本地时间的**ANSI 标准定义的一部分。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。

这些函数验证其参数。 如果*sourceTime*是空指针，或者如果*sourceTime*值为负，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回**NULL**并将**errno**设置为**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**当地时间****_localtime32_localtime64** **_localtime64**|\<time.h>|\<ctime>\<或时间.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
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

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
