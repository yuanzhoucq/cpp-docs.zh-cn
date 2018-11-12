---
title: 时间管理
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: e7b34101e6c09238316d7dc0ebb223ede25d60bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623764"
---
# <a name="time-management"></a>时间管理

使用这些函数获取当前时间并按需对其转换、调整及存储。 当前时间为系统时间。

_ftime 和 localtime 例程使用 TZ 环境变量。 如果未设置 TZ，则运行时库将尝试使用由操作系统指定的时区信息。 如果此信息不可用，则这些函数将使用默认值 PST8PDT。 有关 TZ 的详细信息，请参阅 [_tzset](../c-runtime-library/reference/tzset.md)；另请参阅 [_daylight、timezone 和 _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

### <a name="time-routines"></a>时间例程

|函数|使用|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|将时间从 struct tm 类型转换为字符串。 这些具有 _s 后缀的函数版本更安全。|
|[clock](../c-runtime-library/reference/clock.md)|返回进程已用的时钟时间。|
|[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|将时间从 time_t、__time32_t 或 __time64_t 类型转换为字符串。 这些具有 _s 后缀的函数版本更安全。|
|[difftime、_difftime32、_difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|计算两个时间之差。|[System::DateTime::Subtract](https://msdn.microsoft.com/library/system.datetime.subtract.aspx)|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)，[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|将当前系统时间存储在 struct _timeb 或 struct __timeb64 类型的变量中。这些带有 _s 后缀的函数版本更安全。|
|[_futime、_futime32、_futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|打开文件后设置修改时间|
|[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[gmtime_s、_gmtime32_s、_gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|将时间从 time_t 类型转换为 struct tm 或从 __time64_t 类型转换为 struct tm。这些具有 _s 后缀的函数版本更安全。|
|[localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)、[localtime_s、_localtime32_s、_localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|通过本地更正，将时间从 time_t 类型转换为 struct tm 或从 __time64_t 类型转换为 struct tm。 这些具有 _s 后缀的函数版本更安全。|
|[_mkgmtime、_mkgmtime32、_mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|将时间转换为格林威治标准时间中的日历值。|
|[mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|将时间转换为日历值。|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|以字符串形式返回当前系统日期。 这些具有 _s 后缀的函数版本更安全。|
|[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|将日期时间字符串设置为可在全球范围内使用的格式。|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)， [_strtime_s、_wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|以字符串形式返回当前系统时间。 这些具有 _s 后缀的函数版本更安全。|
|[time、_time32、_time64](../c-runtime-library/reference/time-time32-time64.md)|获取当前系统时间作为 time_t、__time32_t 或 __time64_t 类型。|
|[_tzset](../c-runtime-library/reference/tzset.md)|根据环境时间变量 TZ 设置外部时间变量。|
|[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|使用当前时间或存储在结构中的时间值设置指定文件的修改时间。|

> [!NOTE]
> 在 Microsoft C/C++ 的所有版本（除 Microsoft C/C++ 7.0 版）和 Visual C++ 的所有版本中，时间函数将当前时间返回为自 1970 年 1 月 1 日午夜以来过去的秒数。 在 Microsoft C/C++ 7.0 版中，time 将当前时间返回为自 1899 年 12 月 31 日午夜以来过去的秒数。

> [!NOTE]
> 在 Visual C++ 2005 之前的 Visual C++ 和 Microsoft C/C++ 的版本中，time_t 为 long int（32 位），因此无法用于 2038 年 1 月 19 日 3:14:07 UTC 之后的日期。 现在，time_t 默认等于 __time64_t，但定义 _USE_32BIT_TIME_T 会将 time_t 改为 __time32_t and forces many time functions 改为 call versions that take the 32-bit time_t 的版本。 有关详细信息，请参阅[标准类型](../c-runtime-library/standard-types.md)以及文档中对各时间函数的注释。

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
