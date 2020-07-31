---
title: gmtime_s、_gmtime32_s、_gmtime64_s
ms.date: 4/2/2020
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
- _o__gmtime32_s
- _o__gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: 8cebd2eab1c0a5b650f33ccca1e87a0a8cad1e08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213549"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s、_gmtime32_s、_gmtime64_s

将时间值转换为**tm**结构。 这些是具有安全增强功能的 [_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>参数

*tmDest*<br/>
指向[tm](../../c-runtime-library/standard-types.md)结构的指针。 返回的结构的字段以 UTC 而不是本地时间保存*计时器*参数的计算值。

*sourceTime*<br/>
指向存储时间的指针。 时间表示为自 1970 年 1 月 1 日午夜 (00:00:00)，协调世界时 (UTC) 以来所经过的秒数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则返回值为错误代码。 在 Errno.h 中定义了错误代码；有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>错误条件

|*tmDest*|*sourceTime*|返回|*TmDest*中的值|
|-----------|------------|------------|--------------------|
|**NULL**|any|**EINVAL**|未修改。|
|Not **NULL** （指向有效内存）|**NULL**|**EINVAL**|所有字段都设置为 -1。|
|Not **NULL**|< 0|**EINVAL**|所有字段都设置为 -1。|

对于前两种错误条件，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**_Gmtime32_s**函数将分解*sourceTime*值，并将其存储在以 Time h 定义的**tm**类型的结构中。 结构的地址是在*tmDest*中传递的。 *SourceTime*的值通常是通过调用[time](time-time32-time64.md)函数获取的。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。 C 运行时库假设使用美国规则实现夏令时的计算。

每个结构字段的类型均为 **`int`** ，如下表所示。

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
|**tm_isdst**|对于**gmtime_s**，始终为0。|

使用 **__time64_t**结构的 **_gmtime64_s**允许日期最大表示为23:59:59 年12月31日3000，UTC;而**gmtime32_s**仅表示日期为23:59:59 年1月 2038 18 日，UTC。 1970 年 1 月 1 日午夜是这两个函数的日期范围下限。

**gmtime_s**是计算结果为 **_gmtime64_s**并且**time_t**等效于 **__time64_t**的内联函数。 如果需要强制编译器将**time_t**解释为旧32位**time_t**，可以定义 **_USE_32BIT_TIME_T**。 这样做将导致**gmtime_s**在 **_gmtime32_s**中进行排列。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**gmtime_s**、 **_gmtime32_s** **_gmtime64_s**|\<time.h>|\<ctime> 或 \<time.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
