---
title: _ftime, _ftime32, _ftime64
ms.date: 11/04/2016
api_name:
- _ftime64
- _ftime
- _ftime32
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
helpviewer_keywords:
- ftime64 function
- _ftime64 function
- current time
- _ftime function
- ftime function
- _ftime32 function
- ftime32 function
- time, getting current
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
ms.openlocfilehash: b8cc46a0a5470892e0bdfdcb0918c2757cdaf4c7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956337"
---
# <a name="_ftime-_ftime32-_ftime64"></a>_ftime, _ftime32, _ftime64

获取当前时间。 提供这些函数的更安全版本；请参阅 [_ftime_s、_ftime32_s、_ftime64_s](ftime-s-ftime32-s-ftime64-s.md)。

## <a name="syntax"></a>语法

```C
void _ftime( struct _timeb *timeptr );
void _ftime32( struct __timeb32 *timeptr );
void _ftime64( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>参数

*timeptr*<br/>
指向 **_timeb**、 **__timeb32**或 **__timeb64**结构的指针。

## <a name="remarks"></a>备注

**_Ftime**函数获取当前的本地时间，并将其存储在由*timeptr*指向的结构中。 \\Timeb> 中\<定义了 _timeb、 **__timeb32**和 **__timeb64**结构。 它们包含下表中列出的四个字段。

|字段|描述|
|-|-|
|**dstflag**|如果本地时区目前正在实行夏令时，则为非零。 （请参阅 [_tzset](tzset.md) 了解有关如何确定夏令时的解释。）|
|**millitm**|秒的分数（以毫秒为单位）。|
|**time**|自 1970 年 1 月 1 日午夜 (00: 00:00) 以来的时间（以秒为单位），格式为协调世界时 (UTC)。|
|**timezone**|从东向西，UTC 与本地时间之间的差值（以分钟为单位）。 **时区**值是从全局变量 **_timezone**的值设置的（请参阅 **_tzset**）。|

使用 **__timeb64**结构的 **_ftime64**函数允许在23:59:59 年12月 3000 31 日之前将文件创建日期表示为，而 **_ftime32**只表示日期为23:59:59 年1月 2038 18 日，UTC。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。

**_Ftime**函数等效于 **_ftime64**， **_timeb**包含64位时间，除非定义了 **_USE_32BIT_TIME_T** ，在这种情况下旧行为有效; **_ftime**使用32位时间， **_timeb**包含32位时间。

**_ftime**验证其参数。 如果将 null 指针传递为*timeptr*，则函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数会将**errno**设置为**EINVAL**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_ftime**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime32**|\<sys/types.h> 和 \<sys/timeb.h>|
|**_ftime64**|\<sys/types.h> 和 \<sys/timeb.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_ftime.c
// compile with: /W3
// This program uses _ftime to obtain the current
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

   _ftime( &timebuffer ); // C4996
   // Note: _ftime is deprecated; consider using _ftime_s instead

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
