---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 11/04/2016
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: ee802e9e6ddef839f08cf6dab6573f404328b2c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937760"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

将时间值转换为字符串，并调整本地时区设置。 提供这些函数的更安全版本；请参阅 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)。

## <a name="syntax"></a>语法

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>参数

*sourceTime*<br/>
指向要转换的存储时间的指针。

## <a name="return-value"></a>返回值

指向字符串结果的指针。 如果以下情况，将返回**NULL** ：

- *sourceTime*表示1970年1月1日午夜之前的日期。

- 如果使用 **_ctime32**或 **_Wctime32** ，而*SourceTime*表示23:59:59 年1月 2038 18 日之后的日期（UTC）。

- 如果使用 **_ctime64**或 **_Wctime64** ，而*SourceTime*表示23:59:59 年12月 3000 31 日之后的日期（UTC）。

**ctime**是一个内联函数，其计算结果为 **_ctime64** ， **time_t**等效于 **__time64_t**。 如果需要强制编译器将**time_t**解释为旧的32位**time_t**，可定义 **_USE_32BIT_TIME_T**。 这样做将导致**ctime**计算为 **_ctime32**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

## <a name="remarks"></a>备注

**Ctime**函数将存储为[time_t](../../c-runtime-library/standard-types.md)值的时间值转换为字符串。 *SourceTime*值通常是从对[time](time-time32-time64.md)的调用中获取的，它返回自午夜（00:00:00）起，年1月 1970 1 日（协调世界时（UTC））开始经过的秒数。 返回值字符串正好包含 26 个字符，且格式为：

```Output
Wed Jan 02 02:03:55 1980\n\0
```

使用 24 小时制。 所有字段都具有固定宽度。 换行符 ('\n') 和空字符 ('\0') 占据字符串的最后两个位置。

转换的字符串同时根据本地时区设置进行调整。 有关定义时区环境和全局变量的详细信息，请参阅[time](time-time32-time64.md)、 [_ftime](ftime-ftime32-ftime64.md)和[localtime](localtime-localtime32-localtime64.md)函数，了解有关配置本地时间和[_tzset](tzset.md)函数的详细信息。

调用**ctime**会修改**gmtime**和**localtime**函数使用的单个静态分配的缓冲区。 每次调用这些例程都会破坏上一次调用的结果。 **ctime**使用**asctime**函数共享静态缓冲区。 因此，调用**ctime**会销毁对**asctime**、 **localtime**或**gmtime**的任何以前调用的结果。

**_wctime**和 **_wctime64**是**ctime**和 **_ctime64**的宽字符版本;返回指向宽字符字符串的指针。 否则， **_ctime64**、 **_wctime**和 **_wctime64**的行为与**ctime**完全相同。

这些函数验证其参数。 如果*sourceTime*为 null 指针，或*sourceTime*值为负，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数将返回**NULL** ，并将**Errno**设置为**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> 或 \<wchar.h>|
|**_wctime32**|\<time.h> 或 \<wchar.h>|
|**_wctime64**|\<time.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
