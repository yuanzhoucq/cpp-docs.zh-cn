---
title: mktime、_mktime32、_mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: b0981f33d70945083eacd28eb7517e80b3f2539f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338705"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime、_mktime32、_mktime64

将本地时间转换为日历值。

## <a name="syntax"></a>语法

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>参数

*timeptr*<br/>
有关指向时间结构的指针，请参阅 [asctime](asctime-wasctime.md)。

## <a name="return-value"></a>返回值

**_mktime32**返回编码为[类型time_t](../../c-runtime-library/standard-types.md)的值的指定日历时间。 如果*timeptr*引用 1970 年 1 月 1 日午夜之前的日期，或者如果无法表示日历时间 **，_mktime32**返回 -1 强制转换以键入**time_t**。 使用 **_mktime32**时，如果*timeptr*引用 2038 年 1 月 18 日 23：59：59 之后的日期，则协调通用时间 （UTC）后，它将返回 -1 强制转换以键入**time_t**。

如果*时间点*引用日期 23：59：59，3000 年 12 月 31 日之后的日期 **，_mktime64**将返回 -1 强制转换以键入 **__time64_t。**

## <a name="remarks"></a>备注

**mktime、_mktime32**和 **_mktime64**函数将*timeptr*指向的提供的时间结构（可能不完整）转换为具有规范化值的完全定义的结构，然后将其转换为**time_t**日历时间值。 **_mktime32** 转换后的时间与由 [time](time-time32-time64.md) 函数返回的值具有相同的编码。 忽略*时计*结构**tm_wday**和**tm_yday**组件的原始值，其他组件的原始值不限于其正常范围。

**mktime**是等效于 **_mktime64**的内联函数，除非定义了 **_USE_32BIT_TIME_T，** 在这种情况下，它等效于 **_mktime32**。

调整到 UTC 后 **，_mktime32**处理从 1970 年 1 月 1 日午夜到 2038 年 1 月 18 日 23：59：59 UTC 的日期。 **_mktime64**处理日期从 1970 年 1 月 1 日午夜到 23：59：59，12 月 31 日，3000 年 12 月 31 日。 此调整可能导致这些函数返回 -1（强制转换为**time_t、__time32_t**或 **__time64_t），** 即使您指定的日期在范围内。 **__time32_t** 例如，如果你位于埃及开罗（比 UTC 早两个小时），则首先将从你在 *timeptr* 中指定的日期中减去两个小时；此时这可能会使你的日期超出范围。

这些函数可用于在 tm 结构中进行验证和填充。 如果成功，这些函数将**tm_wday**和**tm_yday**的值设置为适当的，并将其他组件设置为表示指定的日历时间，但其值强制为正常范围。 在确定**tm_mon**和**tm_year**之前，不会设置**tm_mday**的最终值。 指定**tm**结构时间时，将**tm_isdst**字段设置为：

- 零 (0)，指示标准时间有效。

- 大于 0 的值，指示夏令时有效。

- 小于零的值，使用 C 运行时库代码计算有效的是标准时间还是夏令时。

C 运行时库将从 [TZ](tzset.md) 环境变量中确定夏令时行为。 如果未**TZ**设置 TZ，Win32 API 调用[GetTimeZone 信息](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation)用于从操作系统获取夏令时信息。 如果此操作失败，则该库将假设使用用于实现夏令时计算的美国规则。 **tm_isdst**是必填字段。 如果未设置，则未定义其值，并且这些函数的返回值不可预知。 如果*timeptr*指向以前调用[asctime、gmtime](asctime-wasctime.md)或[本地时间](localtime-localtime32-localtime64.md)（或这些函数的变体）返回的**tm**结构，则**tm_isdst**字段包含正确的值。 [gmtime](gmtime-gmtime32-gmtime64.md)

请注意 **，gmtime**和**本地时间**（以及 **_gmtime32**_gmtime32、_gmtime64、_localtime32 和 **_gmtime64****_localtime64）** 使用每个线程的单个缓冲区进行转换。 **_localtime32** 如果向**mktime、_mktime32**或 **_mktime32** **_mktime64**提供此缓冲区，则以前的内容将被销毁。

这些函数将验证其参数。 如果 *timeptr* 是 null 指针，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回 -1 并将**errno**设置为**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>示例输出

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
