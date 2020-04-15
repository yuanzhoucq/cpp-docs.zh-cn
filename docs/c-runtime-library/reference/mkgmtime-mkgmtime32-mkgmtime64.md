---
title: _mkgmtime、_mkgmtime32、_mkgmtime64
description: 描述 _mkgmtime、_mkgmtime32 和 _mkgmtime64 C 运行时库函数，并举例说明如何使用它们。
ms.date: 4/2/2020
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
- _o__mkgmtime32
- _o__mkgmtime64
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: e8b3170fc0413a878777035fd76aac5eefa7b6bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338776"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64

将由**结构** **tm**表示的 UTC 时间转换为由**time_t**类型表示的 UTC 时间。

## <a name="syntax"></a>语法

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>参数

*时间分器*\
指向 UTC 时间的指针，作为要转换**的结构** **tm。**

## <a name="return-value"></a>返回值

表示自 1970 年 1 月 1 日午夜以来在协调通用时间 （UTC） 中经过的秒数的 **__time32_t**或 **__time64_t**数量。 如果日期超过范围（请参阅备注部分），或者输入不能解释为有效时间，则返回值为 -1。

## <a name="remarks"></a>备注

**_mkgmtime32**和 **_mkgmtime64**函数将 UTC 时间转换为表示 UTC 中时间的 **__time32_t**或 **__time64_t**类型。 要将本地时间转换为 UTC 时间，请使用**mktime、_mktime32**和 **_mktime64。** **_mktime32**

**_mkgmtime**是一个内联函数，用于计算到 **_mkgmtime64，time_t**等效于 **__time64_t**。 **time_t** 如果需要强制编译器将**time_t**解释为旧的 32 位**time_t**，则可以定义 **_USE_32BIT_TIME_T**。 我们不推荐它，因为您的应用程序可能在 2038 年 1 月 18 日之后失败，32 位**的最大范围time_t**。 在 64 位平台上根本不允许它。

传入的时间结构按如下方式更改，其方式与 **_mktime**函数更改的方式相同 **：tm_wday**和**tm_yday**字段设置为基于**tm_mday**和**tm_year**的值的新值。 由于时间假定为**UTC，因此**tm_isdst字段将被忽略。

**_mkgmtime32**功能的范围是从 1970 年 1 月 1 日午夜到 UTC 到 2038 年 1 月 18 日 23：59：59，UTC。 **_mkgmtime64**范围为 1970 年 1 月 1 日午夜、UTC 至 23：59：59、12 月 31 日、3000 年 UTC。 范围外日期会导致返回值 -1。 **_mkgmtime**范围取决于是否定义了 **_USE_32BIT_TIME_T。** 如果未定义它（默认值）时，范围与 **_mkgmtime64**相同。 否则，范围将限制为**32**位_mkgmtime32范围。

**gmtime**和**本地时间**都使用公共静态缓冲区进行转换。 如果向 **_mkgmtime**提供此缓冲区，则销毁前面的内容。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="examples"></a>示例

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

下面的示例显示了 _mkgmtime 如何填充不完整**的结构。** 它计算一周和一年中的一天的值。

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)\
[asctime， _wasctime](asctime-wasctime.md)\
[asctime_s，_wasctime_s](asctime-s-wasctime-s.md)\
[gmtime， _gmtime32， _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s，_localtime32_s，_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime， _mktime32， _mktime64](mktime-mktime32-mktime64.md)\
[time、_time32、_time64](time-time32-time64.md)
