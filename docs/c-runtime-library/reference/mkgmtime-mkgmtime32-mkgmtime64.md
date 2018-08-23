---
title: _mkgmtime、_mkgmtime32、_mkgmtime64 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcb587cf5504f661512ccf88cf4f15d0555e2f18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405135"
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64

将 UTC 时间表示为**结构** **tm**为 UTC 时间表示**time_t**类型。

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

*timeptr*<br/>
指向在 UTC 时间的**结构** **tm**要转换。

## <a name="return-value"></a>返回值

类型的数量 **__time32_t**或 **__time64_t**自 1970 年 1 月 1 日，以协调世界时 (UTC) 午夜以来经过的表示的秒数。 如果日期超出范围 （请参阅备注部分） 或输入不能解释为有效的时间，则返回值为-1。

## <a name="remarks"></a>备注

**_Mkgmtime32**和 **_mkgmtime64**函数将转换为 UTC 时间 **__time32_t**或 **__time64_t**类型表示的时间UTC。 若要将本地时间转换为 UTC 时间，使用**mktime**， **_mktime32**，和 **_mktime64**相反。

**_mkgmtime**是内联函数计算结果为 **_mkgmtime64**，和**time_t**等效于 **__time64_t**。 如果需要强制编译器将解释**time_t**为旧的 32 位**time_t**，你可以定义 **_USE_32BIT_TIME_T**。 不建议使用此因为你的应用程序可能会失败后 2038 年 1 月 18 日 (32 位的最大范围**time_t**)，并且它不在任何允许在 64 位平台上。

结构中传递的时间将更改，如下所示，在相同的方式与发生更改时 **_mktime**函数： **tm_wday**和**tm_yday**字段设置为新基于值的值**tm_mday**和**tm_year**。 指定时**tm**结构时间时，请将设置**tm_isdst**字段：

- 零 (0)，指示标准时间有效。

- 大于 0 的值，指示夏令时有效。

- 小于零的值，使用 C 运行时库代码计算有效的是标准时间还是夏令时。

C 运行时库将使用 TZ 环境变量确定正确的夏令时。 如果未设置 TZ，将对操作系统进行查询以获取正确的区域夏令时行为。 **tm_isdst**是必填的字段。 如果未设置，未定义其值和返回值从**mktime**是不可预知的。

范围 **_mkgmtime32**函数为从 1970 年 1 月 1 日午夜到 23:59:59 2038 年 1 月 18 日，UTC UTC。 范围 **_mkgmtime64**为 1970 年 1 月 1 日午夜 UTC 至 23:59:59，3000 年 12 月 31 日，UTC。 超出范围日期将导致返回值-1。 范围 **_mkgmtime**取决于是否 **_USE_32BIT_TIME_T**定义。 如果未定义 （默认值） 的范围是的 **_mkgmtime64**; 否则为范围仅限于的 32 位范围 **_mkgmtime32**。

请注意， **gmtime**和**localtime**使用单个静态分配的缓冲区执行该转换。 如果提供此缓冲区**mkgmtime**，以前的内容会被销毁。

## <a name="example"></a>示例

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

### <a name="sample-output"></a>示例输出

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

以下示例显示如何使用一周中星期和一年中日期的计算值填充不完整的结构。

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

### <a name="output"></a>输出

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
