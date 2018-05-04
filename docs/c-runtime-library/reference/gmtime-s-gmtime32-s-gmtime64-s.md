---
title: gmtime_s、_gmtime32_s、_gmtime64_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b15896ff9ec96ed8dd9867c14d252edaad2c67a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s、_gmtime32_s、_gmtime64_s

时间将值转换为**tm**结构。 这些是具有安全增强功能的 [_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

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
指向[tm](../../c-runtime-library/standard-types.md)结构。 返回的结构字段存储的计算的值*计时器*自变量在 UTC 而不是本地时间。

*sourceTime*<br/>
指向存储时间的指针。 时间表示为自 1970 年 1 月 1 日午夜 (00:00:00)，协调世界时 (UTC) 以来所经过的秒数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则返回值为错误代码。 在 Errno.h 中定义了错误代码；有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>错误条件

|*tmDest*|*sourceTime*|返回|中的值*tmDest*|
|-----------|------------|------------|--------------------|
|**NULL**|任何|**EINVAL**|未修改。|
|不**NULL** （指向有效的内存）|**NULL**|**EINVAL**|所有字段都设置为 -1。|
|不**NULL**|< 0|**EINVAL**|所有字段都设置为 -1。|

对于前两种错误条件，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回**EINVAL**。

## <a name="remarks"></a>备注

**_Gmtime32_s**函数将分解*sourceTime*值并将它存储在类型的结构**tm**在 Time.h 中定义。 结构的地址传递中*tmDest*。 值*sourceTime*通常从调用中获取[时间](time-time32-time64.md)函数。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。 C 运行时库假设使用美国规则实现夏令时的计算。

每个结构字段的类型是**int**下, 表中所示。

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
|**tm_isdst**|始终为 0 的**gmtime_s**。|

**_gmtime64_s**，它使用 **__time64_t**结构，而允许的日期以通过 23:59:59，3000 年 12 月 31 日，UTC; 表示向上**gmtime32_s**仅表示通过日期23:59:59 2038 年 1 月 18日日，UTC。 1970 年 1 月 1 日午夜是这两个函数的日期范围下限。

**gmtime_s**是内联函数计算结果为 **_gmtime64_s**和**time_t**等效于 **__time64_t**。 如果需要强制编译器将解释**time_t**为旧的 32 位**time_t**，你可以定义 **_USE_32BIT_TIME_T**。 这将导致这样做**gmtime_s**为内联到 **_gmtime32_s**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

## <a name="requirements"></a>要求

|例程|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**gmtime_s**|**_gmtime32_s**， **_gmtime64_s**|\<time.h>|\<ctime > 或\<.h >|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
