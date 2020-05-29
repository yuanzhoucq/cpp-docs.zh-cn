---
title: _strtime_s、_wstrtime_s
ms.date: 4/2/2020
api_name:
- _wstrtime_s
- _strtime_s
- _o__strtime_s
- _o__wstrtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: 54828bf894ffc9062125c9680ec087cdf929b1a2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910927"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s、_wstrtime_s

将当前时间复制到缓冲区。 这些版本的 [_strtime、_wstrtime](strtime-wstrtime.md) 具有安全性增强功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*宽限*<br/>
至少为 10 个字节长的缓冲区，将在其中写入时间。

*numberOfElements*<br/>
缓冲区的大小。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

如果出现错误条件，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果失败，则返回值为错误代码。 错误代码在 ERRNO.H 中定义；有关此函数生成的确切错误，请参阅下表。 有关错误代码的详细信息，请参阅 [errno 常量](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>错误条件

|*宽限*|*numberOfElements*|返回|*缓冲区*内容|
|--------------|------------------------|------------|--------------------------|
|**Null**|（任意数值）|**EINVAL**|未修改|
|Not **NULL** （指向有效的缓冲区）|0|**EINVAL**|未修改|
|Not **NULL** （指向有效的缓冲区）|0 < 大小 < 9|**EINVAL**|空字符串|
|Not **NULL** （指向有效的缓冲区）|大小 > 9|0|注解中指定的当前时间格式|

## <a name="security-issues"></a>安全问题

如果*numberOfElements*参数大于9，则为缓冲区传入无效的非**NULL**值将导致访问冲突。

传递*numberOfElements*的值大于缓冲区的实际大小将导致缓冲区溢出。

## <a name="remarks"></a>备注

这些函数为[_strtime](strtime-wstrtime.md)和[_wstrtime](strtime-wstrtime.md)提供更安全的版本。 **_Strtime_s**函数将当前的本地时间复制到*timestr*所指向的缓冲区中。 此时间的格式为**hh： mm： ss** ，其中， **hh**是表示小时的两位数字，以24小时表示法表示， **mm**是表示分钟后的分钟数的两位数， **ss**是表示秒的两位数。 例如，字符串**18:23:44**表示23分钟到 6 p.m 之前的44秒。 缓冲区必须至少为 9 个字节长；实际大小由第二个参数指定。

**_wstrtime**是 **_strtime**的宽字符版本;**_wstrtime**的参数和返回值是宽字符字符串。 否则这些函数具有相同行为。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射：

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<time.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
