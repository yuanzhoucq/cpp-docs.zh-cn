---
title: _strdate_s、_wstrdate_s
description: _strdate_s 和 _wstrdate_s 是用于将当前日期放入缓冲区的 _strdate 和 _wstrdate 函数的安全 CRT 版本。
ms.date: 11/01/2019
api_name:
- _strdate_s
- _wstrdate_s
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
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: 7d04c134fcd19753ac0cecf8cc3b87e902d92e83
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625762"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s、_wstrdate_s

将当前系统日期复制到缓冲区。 这些函数是[_strdate、_wstrdate](strdate-wstrdate.md)的版本，具有[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>参数

*缓冲区*\
指向缓冲区的指针，用于放置格式化的日期字符串。

*大小*\
缓冲区的大小（以字符为单位）。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果出现故障，则返回值为错误代码。 错误代码在 ERRNO.H 中定义；有关此函数生成的确切错误，请参阅下表。 有关错误代码的详细信息，请参阅 [errno](../../c-runtime-library/errno-constants.md)。

## <a name="error-conditions"></a>错误条件

|*buffer*|*size*|返回|*缓冲区*内容|
|--------------|------------------------|------------|--------------------------|
|**NULL**|（任意数值）|**EINVAL**|未修改|
|Not **NULL** （指向有效的缓冲区）|0|**EINVAL**|未修改|
|Not **NULL** （指向有效的缓冲区）|0 <*大小*< 9|**EINVAL**|空字符串|
|Not **NULL** （指向有效的缓冲区）|*大小*> = 9|0|注解中指定的当前日期格式|

## <a name="security-issues"></a>安全问题

如果*size*参数大于9，则为*缓冲区*传入无效的非 NULL 值会导致访问冲突。

如果传递的*大小*值大于*缓冲区*的实际大小，则会导致缓冲区溢出。

## <a name="remarks"></a>备注

这些函数提供更安全的 **_strdate**和 **_wstrdate**版本。 **_Strdate_s**函数将当前系统日期复制到*缓冲区*所指向的缓冲区。 它的格式 `mm/dd/yy`，其中 `mm` 是两位数的月份，`dd` 是两位数的日期，`yy` 是年份的最后两位数字。 例如，字符串 `12/05/99` 表示 1999 年 12 月 5 日。 缓冲区的长度必须至少为9个字符。

**_wstrdate_s**是 **_strdate_s**的宽字符版本; **_wstrdate_s**的参数和返回值是宽字符字符串。 否则这些函数具有相同行为。

如果*buffer*为**空**指针，或*大小*少于9个字符，则将调用无效的参数处理程序。 它在[参数验证](../../c-runtime-library/parameter-validation.md)中进行了介绍。 如果允许执行继续，则这些函数将返回-1。 如果缓冲区为**NULL**或者*size*小于或等于0，则将**errno**设置为**EINVAL** 。 或者，如果*size*小于9，则它们将**Errno**设置为**ERANGE** 。

在C++中，模板重载简化了这些函数的使用。 重载可以自动推断缓冲区长度，从而无需指定*大小*自变量。 而且，它们可以自动将不安全的函数替换为更新、更安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射：

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> 或 \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>示例

请参阅 [time](time-time32-time64.md) 的示例。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)\
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)\
[time、_time32、_time64](time-time32-time64.md)\
[_tzset](tzset.md)
