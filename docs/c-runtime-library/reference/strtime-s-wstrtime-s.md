---
title: _strtime_s、_wstrtime_s
ms.date: 11/04/2016
apiname:
- _wstrtime_s
- _strtime_s
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
ms.openlocfilehash: 579c4a99b52c66bd14cea947eaa1f301cc1127e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375322"
---
# <a name="strtimes-wstrtimes"></a>_strtime_s、_wstrtime_s

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

*buffer*<br/>
至少为 10 个字节长的缓冲区，将在其中写入时间。

*numberOfElements*<br/>
缓冲区的大小。

## <a name="return-value"></a>返回值

如果成功，则返回 0。

如果出现错误条件，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果失败，则返回值为错误代码。 错误代码在 ERRNO.H 中定义；有关此函数生成的确切错误，请参阅下表。 有关错误代码的详细信息，请参阅 [errno 常量](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>错误条件

|*buffer*|*numberOfElements*|返回|内容*缓冲区*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|（任意数值）|**EINVAL**|未修改|
|不**NULL** （指向有效的缓冲区）|0|**EINVAL**|未修改|
|不**NULL** （指向有效的缓冲区）|0 < 大小 < 9|**EINVAL**|空字符串|
|不**NULL** （指向有效的缓冲区）|大小 > 9|0|注解中指定的当前时间格式|

## <a name="security-issues"></a>安全性问题

传入无效非**NULL**值的缓冲区将导致访问冲突，如果*numberOfElements*参数大于 9。

为传递值*numberOfElements*大于缓冲区的实际大小将导致缓冲区溢出。

## <a name="remarks"></a>备注

这些函数提供更多安全版本[_strtime](strtime-wstrtime.md)并[_wstrtime](strtime-wstrtime.md)。 **_Strtime_s**函数将当前的本地时间复制到由指向的缓冲区*timestr*。 时间格式为**hh: mm:** 其中**hh**是两位数字，表示 24 小时制的小时**mm**是两位数表示小时，并且分钟**ss**是两位数表示秒。 例如，字符串**18:23:44**表示 23 分 44 秒下午 6 点 缓冲区必须至少为 9 个字节长；实际大小由第二个参数指定。

**_wstrtime**是宽字符版本 **_strtime**; 的自变量和返回值 **_wstrtime**都是宽字符字符串。 否则这些函数具有相同行为。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射：

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<time.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
