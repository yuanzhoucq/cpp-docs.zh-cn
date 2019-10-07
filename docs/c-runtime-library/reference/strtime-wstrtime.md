---
title: _strtime、_wstrtime
ms.date: 11/04/2016
api_name:
- _wstrtime
- _strtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: ea4a2b304dc30ec167f8a9094bcf278ff0d31f77
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946564"
---
# <a name="_strtime-_wstrtime"></a>_strtime、_wstrtime

将时间复制到缓冲区。 这些函数的更安全版本已经发布；请参阅 [_strtime_s、_wstrtime_s](strtime-s-wstrtime-s.md)。

## <a name="syntax"></a>语法

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*timestr*<br/>
时间字符串。

## <a name="return-value"></a>返回值

返回一个指向生成的字符串*timestr*的指针。

## <a name="remarks"></a>备注

**_Strtime**函数将当前的本地时间复制到*timestr*指向的缓冲区中。 此时间的格式为**hh： mm： ss** ，其中， **hh**是表示小时的两位数字，以24小时表示法表示， **mm**是表示分钟后的分钟数的两位数， **ss**是表示秒的两位数。 例如，字符串**18:23:44**表示23分钟到 6 p.m 之前的44秒。 缓冲区长度必须至少为 9 个字节。

**_wstrtime**是 **_strtime**的宽字符版本; **_wstrtime**的参数和返回值是宽字符字符串。 否则这些函数具有相同行为。 如果*timestr*为**NULL**指针或*timestr*的格式不正确，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行此操作，则这些函数将返回**null** ，并**将 Errno**设置为**EINVAL**如果*timestr*为**null** ，则将设置为，如果*ERANGE*的格式不正确，则将**errno**设置为**timestr** 。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
