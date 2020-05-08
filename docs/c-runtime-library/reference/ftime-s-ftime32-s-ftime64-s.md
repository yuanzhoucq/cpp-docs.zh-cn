---
title: _ftime_s、_ftime32_s、_ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
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
ms.openlocfilehash: a77d149f367c7f565141fbc3be1db1bfc3f3f362
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909963"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s、_ftime32_s、_ftime64_s

获取当前时间。 这些是具有安全增强功能的 [_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 的版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>参数

*timeptr*<br/>
指向 **_timeb**、 **__timeb32**或 **__timeb64**结构的指针。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。 如果*timeptr*为**NULL**，则返回值为**EINVAL**。

## <a name="remarks"></a>备注

**_Ftime_s**函数获取当前的本地时间，并将其存储在*timeptr*所指向的结构中。 **_Timeb**、 **__timeb32**和 **__timeb64**结构在 sys\timeb.h 中定义。 它们包含下表中列出的四个字段。

|字段|说明|
|-|-|
|**dstflag**|如果本地时区目前正在实行夏令时，则为非零。 （请参阅 [_tzset](tzset.md) 了解有关如何确定夏令时的解释。）|
|**millitm**|秒的分数（以毫秒为单位）。|
|**time**|自 1970 年 1 月 1 日午夜 (00: 00:00) 以来的时间（以秒为单位），格式为协调世界时 (UTC)。|
|**时区**|从东向西，UTC 与本地时间之间的差值（以分钟为单位）。 **时区**值是从全局变量 **_timezone**的值设置的（请参阅 **_tzset**）。|

使用 **__timeb64**结构的 **_ftime64_s**函数允许文件创建日期在23:59:59 年12月31日3000，UTC;而 **_ftime32_s**仅表示日期为23:59:59 年1月 2038 18 日，UTC。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。

**_Ftime_s**函数等效于 **_ftime64_s**， **_timeb**包含64位时间，除非定义了 **_USE_32BIT_TIME_T** ，在这种情况下旧行为有效;**_ftime_s**使用32位时间， **_timeb**包含32位时间。

**_ftime_s**验证其参数。 如果将 null 指针传递为*timeptr*，则函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数会将**errno**设置为**EINVAL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> 和 \<sys/timeb.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
