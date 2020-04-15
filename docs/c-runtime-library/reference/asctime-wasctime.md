---
title: asctime、_wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: bda14f3b6046378ad23148371f354bb910163d3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350475"
---
# <a name="asctime-_wasctime"></a>asctime、_wasctime

将**tm**时间结构转换为字符串。 提供这些函数的更多安全版本；请参阅 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

## <a name="syntax"></a>语法

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>参数

*timeptr*<br/>
时间/日期结构。

## <a name="return-value"></a>返回值

**asctime**返回指向字符串结果的指针;**_wasctime**返回指向宽字符字符串结果的指针。 无错误返回值。

## <a name="remarks"></a>备注

提供这些函数的更多安全版本；请参阅 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

**asctime**函数将存储为结构的时间转换为字符串。 *时间点*值通常从对**gmtime**或**本地时间的**调用中获得，这两个调用都会返回指向 TM**结构的**指针，该指针在"时代"中定义。H。

|timeptr 成员|“值”|
|--------------------|-----------|
|**tm_hour**|午夜起（0-23）以来的营业时间|
|**tm_isdst**|如果夏令时生效，则为正；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。|
|**tm_mday**|月日 （1-31）|
|**tm_min**|一小时后几分钟 （0-59）|
|**tm_mon**|月（0-11;1 月 = 0）|
|**tm_sec**|一秒后秒 （0-59）|
|**tm_wday**|星期一（0-6;周日 = 0）|
|**tm_yday**|一年日（0-365;1 月 1 日 = 0）|
|**tm_year**|年（当前年份减去 1900）|

转换的字符串同时根据本地时区设置进行调整。 有关配置本地时间的信息，请参阅 [time](time-time32-time64.md)、[_ftime](ftime-ftime32-ftime64.md) 和 [localtime](localtime-localtime32-localtime64.md) 函数，有关定义时区环境和全局变量的信息，请参阅 [_tzset](tzset.md)。

**asctime**生成的字符串结果正好包含 26 个字符，并且具有窗体`Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小时制。 所有字段都具有固定宽度。 换行符和空字符占据字符串的最后两个位置。 **asctime**使用单个静态分配的缓冲区来保存返回字符串。 每次调用此函数都会破坏上一次调用的结果。

**_wasctime**是一个宽字符版本的**asctime。** **_wasctime**和**asctime**行为相同。

这些函数验证其参数。 如果*timeptr*是空指针，或者如果它包含范围外的值，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回**NULL**并将**errno**设置到**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> 或 \<wchar.h>|

## <a name="example"></a>示例

此程序将系统时间置于长整数**aclock**中，将其转换为结构**新时间**，然后将其转换为字符串形式以进行输出，使用**asctime**函数。

```C
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

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
