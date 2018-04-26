---
title: localtime、_localtime32、_localtime64 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32b462dfbe794d1817fa727736452e961a2b1dfd
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="localtime-localtime32-localtime64"></a>localtime、_localtime32、_localtime64

转换时间值并更正本地时区。 这些函数的更安全版本已经可用；请参阅 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)。

## <a name="syntax"></a>语法

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>参数

*sourceTime*<br/>
指向存储时间的指针。

## <a name="return-value"></a>返回值

返回指向结构结果的指针或**NULL**如果日期传递给函数：

- 1970 年 1 月 1 日午夜前。

- 后 03:14:07，2038 年 1 月 19 日，UTC (使用 **_time32**和**time32_t**)。

- 23:59:59，3000 年 12 月 31 日，UTC 之后 (使用 **_time64**和 **__time64_t**)。

**_localtime64**，它使用 **__time64_t**结构，而允许的日期以通过 23:59:59，3000 年 12 月 31 日，协调世界时 (UTC) 表示向上 **_localtime32**表示到 23:59:59 2038 年 1 月 18 日，UTC 日期。

**localtime**是内联函数计算结果为 **_localtime64**，和**time_t**等效于 **__time64_t**。 如果需要强制编译器将解释**time_t**为旧的 32 位**time_t**，你可以定义 **_USE_32BIT_TIME_T**。 这将导致这样做**localtime**计算结果为 **_localtime32**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

结构类型的字段[tm](../../c-runtime-library/standard-types.md)存储下面的值，其中每个**int**:

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

## <a name="remarks"></a>备注

**Localtime**函数将存储为时间为[time_t](../../c-runtime-library/standard-types.md)值并将结果存储在类型的结构[tm](../../c-runtime-library/standard-types.md)。 **长**值*sourceTime*表示自午夜以来经过的秒 (00: 00:00)、 1970 年 1 月 1 日，UTC。 此值通常从获取[时间](time-time32-time64.md)函数。

这两个 32 位和 64 位版本的[gmtime](gmtime-gmtime32-gmtime64.md)， [mktime](mktime-mktime32-mktime64.md)， [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)，和**localtime**所有使用单个**tm**每个线程的转换结构。 每次调用这些例程都会破坏上一次调用的结果。

**localtime**更正为本地时区，如果用户先设置全局环境变量**TZ**。 当**TZ**设置，其他三个环境变量 (**_timezone**， **_daylight**，和 **_tzname**) 以及自动设置。 如果**TZ**未设置变量， **localtime**尝试使用控制面板中的日期/时间应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](tzset.md)。 **TZ**是 Microsoft 扩展和不属于的 ANSI 标准定义**localtime**。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。

这些函数验证其参数。 如果*sourceTime*是 null 指针，或如果*sourceTime*值为负，则这些函数调用无效参数处理程序中中, 所述[参数验证](../../c-runtime-library/parameter-validation.md). 如果允许执行继续，函数将返回**NULL**并设置**errno**到**EINVAL**。

## <a name="requirements"></a>要求

|例程|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**localtime**， **_localtime32**， **_localtime64**|\<time.h>|\<ctime > 或\<.h >|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
