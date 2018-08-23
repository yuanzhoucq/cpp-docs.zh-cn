---
title: _strdate_s、_wstrdate_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strdate_s
- _wstrdate_s
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
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4e9ff3783fc7a89e7af42ebf283209c034c0d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414306"
---
# <a name="strdates-wstrdates"></a>_strdate_s、_wstrdate_s

将当前系统日期复制到缓冲区。 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [_strdate、_wstrdate](strdate-wstrdate.md) 具有安全性增强功能。

## <a name="syntax"></a>语法

```C
errno_t _strdate_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t numberOfElements
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

*buffer*<br/>
指向缓冲区的指针将使用格式化的日期字符串填充。

*numberOfElements*<br/>
缓冲区的大小。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码在 ERRNO.H 中定义；有关此函数生成的确切错误，请参阅下表。 有关错误代码的详细信息，请参阅 [errno](../../c-runtime-library/errno-constants.md)。

## <a name="error-conditions"></a>错误条件

|*buffer*|*numberOfElements*|返回|内容*缓冲区*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|（任意数值）|**EINVAL**|未修改|
|不**NULL** （指向有效的缓冲区）|0|**EINVAL**|未修改|
|不**NULL** （指向有效的缓冲区）|0 < *numberOfElements* < 9|**EINVAL**|空字符串|
|不**NULL** （指向有效的缓冲区）|*numberOfElements* > = 9|0|注解中指定的当前日期格式|

## <a name="security-issues"></a>安全性问题

传递中的无效非**NULL**值缓冲区会导致访问冲突，如果*numberOfElements*参数大于 9。

传递大小的值大于的实际大小*缓冲区*将导致缓冲区溢出。

## <a name="remarks"></a>备注

这些函数提供更多安全版本 **_strdate**和 **_wstrdate**。 **_Strdate_s**函数将当前系统日期复制到通过指向的缓冲区*缓冲区*格式化**mm**/**dd** / **yy**，其中**mm**是两个数字表示的月**dd**是两个数字表示天，和**yy**是年份的最后两位数。 例如，在字符串**12/05/99**表示 1999 年 12 月 5 日。 缓冲区长度必须至少为 9 个字符。

**_wstrdate_s**是宽字符版本的 **_strdate_s**; 的自变量和返回值 **_wstrdate_s**是宽字符字符串。 否则这些函数具有相同行为。

如果*缓冲区*是**NULL**指针，或如果*numberOfElements*小于 9 个字符，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回-1 并设置**errno**到**EINVAL**如果缓冲区已**NULL**或如果*numberOfElements*小于或等于 0 或一组**errno**到**ERANGE**如果*numberOfElements*小于 9。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mapping"></a>一般文本例程映射：

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

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
