---
title: _strdate_s、_wstrdate_s
description: _strdate_s和_wstrdate_s是将当前日期放入缓冲区_strdate和_wstrdate函数的安全 CRT 版本。
ms.date: 4/2/2020
api_name:
- _strdate_s
- _wstrdate_s
- _o__strdate_s
- _o__wstrdate_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b4d977ba3546eae17218c63b1786fd26c784d340
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359822"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s、_wstrdate_s

将当前系统日期复制到缓冲区。 这些功能是_strdate的版本[，_wstrdate](strdate-wstrdate.md)具有[CRT 中安全功能中所述的安全](../../c-runtime-library/security-features-in-the-crt.md)增强功能。

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
缓冲区的大小（以字符单位为单位）。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果发生故障，返回值是错误代码。 错误代码在 ERRNO.H 中定义；有关此函数生成的确切错误，请参阅下表。 有关错误代码的详细信息，请参阅 [errno](../../c-runtime-library/errno-constants.md)。

## <a name="error-conditions"></a>错误条件

|*缓冲区*|*大小*|返回|*缓冲区*的内容|
|--------------|------------------------|------------|--------------------------|
|**空**|（任意数值）|**埃因瓦尔**|未修改|
|非**NULL（** 指向有效缓冲区）|0|**埃因瓦尔**|未修改|
|非**NULL（** 指向有效缓冲区）|0 <*尺寸*< 9|**埃因瓦尔**|空字符串|
|非**NULL（** 指向有效缓冲区）|*大小*>= 9|0|注解中指定的当前日期格式|

## <a name="security-issues"></a>安全问题

如果*大小*参数大于 9，则为*缓冲区*传入无效的非 NULL 值会导致访问冲突。

传递大于*缓冲区*实际大小*的值*会导致缓冲区溢出。

## <a name="remarks"></a>备注

这些函数提供了更安全的 **_strdate**和 **_wstrdate**版本。 **_strdate_s**函数将当前系统日期复制到*缓冲区*指向的缓冲区。 它的格式`mm/dd/yy`，其中`mm`是两位数的月份，`dd`是两位数的一天，是`yy`一年中的最后两位数字。 例如，字符串 `12/05/99` 表示 1999 年 12 月 5 日。 缓冲区必须至少为九个字符长。

**_wstrdate_s**是 **_strdate_s**的宽字符版本;**_wstrdate_s**的参数和返回值是宽字符字符串。 否则这些函数具有相同行为。

当*缓冲区*是**NULL**指针，或者*大小*小于 9 个字符时，将调用无效的参数处理程序。 参数[验证](../../c-runtime-library/parameter-validation.md)中对此进行了描述。 如果允许继续执行，这些函数将返回 -1。 如果缓冲区为**NULL**或*大小*小于或等于 0，则它们将**errno**设置为**EINVAL。** 或者，如果*大小*小于 9，他们会将**errno**设置为**ERANGE。**

在C++，这些函数的使用通过模板重载简化。 重载可以自动推断缓冲区长度，从而无需指定*大小*参数。 而且，它们还可以用更新、更安全的对应函数自动替换不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>通用文本例程映射：

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> 或 \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>示例

请参阅 [time](time-time32-time64.md) 的示例。

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)\
[asctime_s，_wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s，_localtime32_s，_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime， _mktime32， _mktime64](mktime-mktime32-mktime64.md)\
[时间，_time32，_time64](time-time32-time64.md)\
[_tzset](tzset.md)
