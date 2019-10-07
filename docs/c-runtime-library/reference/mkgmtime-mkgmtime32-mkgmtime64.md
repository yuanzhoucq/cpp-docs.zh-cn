---
title: _mkgmtime、_mkgmtime32、_mkgmtime64
ms.date: 11/04/2016
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
ms.openlocfilehash: fcd1e3fdcca37d7e5bb381c234a6d8555ce2766c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951673"
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

*timeptr*<br/>
一个指针，它指向作为要转换的**struct** **tm**的 UTC 时间。

## <a name="return-value"></a>返回值

类型为 **__time32_t**或 **__time64_t**的数量，表示自1970年1月1日午夜起经过协调世界时（UTC）的秒数。 如果日期超出范围（请参见 "备注" 部分）或输入不能解释为有效时间，则返回值为-1。

## <a name="remarks"></a>备注

**_Mkgmtime32**和 **_MKGMTIME64**函数将 utc 时间转换为表示 utc 时间的 **__time32_t**或 **__time64_t**类型。 若要将本地时间转换为 UTC 时间，请改用**mktime**、 **_mktime32**和 **_mktime64** 。

**_mkgmtime**是计算结果为 **_mkgmtime64**的内联函数，而**time_t**等效于 **__time64_t**。 如果需要强制编译器将**time_t**解释为旧的32位**time_t**，可定义 **_USE_32BIT_TIME_T**。 不建议这样做，因为应用程序可能会在2038年1月18日后失败（32位**time_t**的最大范围），并且在64位平台上根本不允许这样做。

传入的时间结构将按如下方式更改，其方式与它们在 **_mktime**函数中的更改相同： **tm_wday**和**tm_yday**字段将根据**tm_mday**和**tm_year**的值设置为新值。 指定**tm**结构时间时，请将 " **tm_isdst** " 字段设置为：

- 零 (0)，指示标准时间有效。

- 大于 0 的值，指示夏令时有效。

- 小于零的值，使用 C 运行时库代码计算有效的是标准时间还是夏令时。

C 运行时库将使用 TZ 环境变量确定正确的夏令时。 如果未设置 TZ，将对操作系统进行查询以获取正确的区域夏令时行为。 **tm_isdst**是必填字段。 如果未设置，则未定义其值，并且**mktime**中的返回值是不可预知的。

**_Mkgmtime32**函数的范围是从1970年1月1日午夜23:59:59 到年1月18日（2038，utc）。 **_Mkgmtime64**的范围是从1970年1月1日午夜，utc 到23:59:59，年12月 3000 31 日。 超出范围的日期将导致返回值-1。 **_Mkgmtime**的范围取决于是否定义了 **_USE_32BIT_TIME_T** 。 如果未定义（默认值），则范围为 **_mkgmtime64**;否则，范围限制为32位的 **_mkgmtime32**范围。

请注意， **gmtime**和**localtime**使用单个静态分配的缓冲区进行转换。 如果向**mkgmtime**提供此缓冲区，则会销毁以前的内容。

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

### <a name="output"></a>Output

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
