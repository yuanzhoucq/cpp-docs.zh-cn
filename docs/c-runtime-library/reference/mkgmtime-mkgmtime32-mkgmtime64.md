---
title: _mkgmtime、_mkgmtime32、_mkgmtime64
description: 介绍 _mkgmtime、_mkgmtime32 和 _mkgmtime64 C 运行时库函数，并提供有关如何使用这些函数的示例。
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4b20073a2022c7da59a5e224a04051901b7b8a4f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914657"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64

将由**struct** **TM**表示的 utc 时间转换为**TIME_T**类型所表示的 utc 时间。

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

*timeptr*\
一个指针，它指向作为要转换的**struct** **tm**的 UTC 时间。

## <a name="return-value"></a>返回值

类型 **__time32_t**或 **__time64_t**的数量，表示自1970年1月1日午夜以来经过协调世界时（UTC）的秒数。 如果日期超出范围（请参见 "备注" 部分）或输入不能解释为有效时间，则返回值为-1。

## <a name="remarks"></a>备注

**_Mkgmtime32**和 **_MKGMTIME64**函数将 UTC 时间转换为表示 utc 时间的 **__time32_t**或 **__time64_t**类型。 若要将本地时间转换为 UTC 时间，请改用**mktime**、 **_mktime32**和 **_mktime64** 。

**_mkgmtime**是计算结果为 **_mkgmtime64**的内联函数， **time_t**等效于 **__time64_t**。 如果需要强制编译器将**time_t**解释为旧32位**time_t**，可以定义 **_USE_32BIT_TIME_T**。 不建议这样做，因为应用程序可能会在2038年1月18日后失败，32位**time_t**的最大范围。 在64位平台上根本不允许这样做。

传入的时间结构按如下方式更改，其方式与 **_mktime**函数更改的时间结构相同： " **tm_wday** " 和 " **tm_yday** " 字段设置为基于**tm_mday**和**tm_year**的值的新值。 由于时间采用 UTC 格式，因此将忽略**tm_isdst**字段。

**_Mkgmtime32**函数的范围是从1970年1月1日午夜23:59:59 到年1月18日（2038，utc）。 **_Mkgmtime64**的范围是从1970年1月1日午夜到，utc 23:59:59 为，12月 3000 31 日，utc。 超出范围的日期将导致返回值-1。 **_Mkgmtime**的范围取决于是否定义了 **_USE_32BIT_TIME_T** 。 如果未定义（默认值），则范围与 **_mkgmtime64**相同。 否则，范围限制为32位范围内的 **_mkgmtime32**。

**Gmtime**和**localtime**都使用通用静态缓冲区进行转换。 如果向 **_mkgmtime**提供此缓冲区，则会销毁以前的内容。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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

下面的示例演示如何 **_mkgmtime**填写不完整的结构。 它计算每周和每年的值。

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
[asctime、_wasctime](asctime-wasctime.md)\
[asctime_s，_wasctime_s](asctime-s-wasctime-s.md)\
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s、_gmtime32_s _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s、_localtime32_s _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)\
[time、_time32、_time64](time-time32-time64.md)
