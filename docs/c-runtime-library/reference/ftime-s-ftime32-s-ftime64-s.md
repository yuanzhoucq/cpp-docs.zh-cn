---
title: _ftime_s、_ftime32_s、_ftime64_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
dev_langs:
- C++
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a23b31fb88b60b05e587bf62ab07ec7e72de869
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402983"
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s、_ftime32_s、_ftime64_s

获取当前时间。 这些是具有安全增强功能的 [_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>参数

*timeptr*<br/>
指向 **_timeb**， **__timeb32**，或 **__timeb64**结构。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。 如果*timeptr*是**NULL**，则返回值是**EINVAL**。

## <a name="remarks"></a>备注

**_Ftime_s**函数获取当前本地时间，并将其存储在通过指向的结构*timeptr*。 **_Timeb**， **__timeb32**，和 **__timeb64** SYS\Timeb.h 中定义结构。 它们包含下表中列出的四个字段。

|字段|描述|
|-|-|
|**dstflag**|如果本地时区目前正在实行夏令时，则为非零。 （请参阅 [_tzset](tzset.md) 了解有关如何确定夏令时的解释。）|
|**millitm**|秒的分数（以毫秒为单位）。|
|**time**|自 1970 年 1 月 1 日午夜 (00: 00:00) 以来的时间（以秒为单位），格式为协调世界时 (UTC)。|
|**timezone**|从东向西，UTC 与本地时间之间的差值（以分钟为单位）。 值**时区**设置全局变量的值从 **_timezone** (请参阅 **_tzset**)。|

**_Ftime64_s**函数，使用 **__timeb64**结构，请允许文件创建的日期以向上表示通过 23:59:59，3000 年 12 月 31 日，UTC; 而 **_ftime32_s**仅表示到 23:59:59 2038 年 1 月 18 日，UTC 日期。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。

**_Ftime_s**函数等同于 **_ftime64_s**，和 **_timeb**包含 64 位时间，除非 **_USE_32BIT_TIME_T**是定义，在这种情况下这一旧行为已生效;**_ftime_s**使用 32 位时间和 **_timeb**包含 32 位时间。

**_ftime_s**验证其参数。 如果传递 null 指针作为*timeptr*，函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将设置**errno**到**EINVAL**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> 和 \<sys/timeb.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime64_s( &timebuffer );

    time1 = timebuffer.time;
    millitm1 = timebuffer.millitm;
    timezone1 = timebuffer.timezone;
    dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
