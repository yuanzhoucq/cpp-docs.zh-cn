---
title: "时间管理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "日期, 运行时库成员"
  - "时间, 时间管理"
  - "日期函数"
  - "时间函数"
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# 时间管理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用这些函数获取当前时间并按需对其转换、调整及存储。 当前时间为系统时间。  
  
 `_ftime`  和 `localtime` 例程使用 `TZ` 环境变量。 如果未设置 `TZ`，则运行时库将尝试使用由操作系统指定的时区信息。 如果此信息不可用，则这些函数将使用默认值 PST8PDT。 有关 `TZ` 的详细信息，请参阅 [\_tzset](../c-runtime-library/reference/tzset.md)；另请参阅 [\_daylight、timezone 和 \_tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。  
  
### 时间例程  
  
|函数|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[asctime、\_wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime\_s、\_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|将时间从类型 `struct tm` 转换为字符串。 这些具有 `_s` 后缀的函数版本更安全。|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)、[System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)、[System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)、[System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)、[System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[clock](../c-runtime-library/reference/clock.md)|返回进程已用的时钟时间。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)，[\_ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|将时间从类型 `time_t`、`__time32_t` 或 `__time64_t` 转换为字符串。 这些具有 `_s` 后缀的函数版本更安全。|[System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)、[System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)、[System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)、[System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)|  
|[difftime, \_difftime32, \_difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|计算两个时间之差。|[System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[\_ftime, \_ftime32, \_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)，[\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|将当前系统时间存储在 `struct _timeb` 或 `struct``__timeb64` 类型的变量中。这些带有 `_s` 后缀的函数版本更安全。|[System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)|  
|[\_futime、\_futime32、\_futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|打开文件后设置修改时间|[System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx)、[System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx)、[System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)|  
|[gmtime、\_gmtime32、\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|将时间从类型 `time_t` 转换为 `struct tm` 或从类型 `__time64_t` 转换为 `struct tm`。这些具有 `_s` 后缀的函数版本更安全。|[System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx)、[System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)|  
|[localtime、\_localtime32、\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime\_s, \_localtime32\_s, \_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|使用本地更正将时间从类型 `time_t` 转换为 `struct tm` 或从类型 `__time64_t` 转换为 `struct tm`。 这些具有 `_s` 后缀的函数版本更安全。|[System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)|  
|[\_mkgmtime、\_mkgmtime32、\_mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|将时间转换为格林威治标准时间中的日历值。|[System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)|  
|[mktime、\_mktime32、\_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|将时间转换为日历值。|[System::DateTime::DateTime](Overload:System.DateTime.)|  
|[\_strdate, \_wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [\_strdate\_s、\_wstrdate\_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|以字符串形式返回当前系统日期。 这些具有 `_s` 后缀的函数版本更安全。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|将日期时间字符串设置为可在全球范围内使用的格式。|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)、[System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)、[System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)、[System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)、[System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[\_strtime、\_wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)，[\_strtime\_s、\_wstrtime\_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|以字符串形式返回当前系统时间。 这些具有 `_s` 后缀的函数版本更安全。|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)、[System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)、[System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)、[System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)、[System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[time、\_time32、\_time64](../c-runtime-library/reference/time-time32-time64.md)|以 `time_t`、 `__time32_t` 类型或 `__time64_t` 类型获取当前系统时间。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_tzset](../c-runtime-library/reference/tzset.md)|根据环境时间变量 `TZ` 设置外部时间变量。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_utime、\_utime32、\_utime64、\_wutime、\_wutime32、\_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|使用当前时间或存储在结构中的时间值设置指定文件的修改时间。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
> [!NOTE]
>  在 Microsoft C\/C\+\+ 的所有版本（除 Microsoft C\/C\+\+ 7.0 版）和 Visual C\+\+ 的所有版本中，时间函数将当前时间返回为自 1970 年 1 月 1 日午夜以来过去的秒数。 在 Microsoft C\/C\+\+ 7.0 版中，`time`  将当前时间返回为自 1899 年 12 月 31 日午夜以来过去的秒数。  
  
> [!NOTE]
>  在 Visual C\+\+ 2005 之前的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 和 Microsoft C\/C\+\+ 的版本中，`time_t`  为 `long int` （32 位），因此无法用于 2038 年 1 月 19 日 3:14:07 UTC 之后的日期。 现在，`time_t`  默认等于 `__time64_t`，但定义 `_USE_32BIT_TIME_T`  会将 `time_t`  改为 `__time32_t` ，并强制许多时间函数调用采用 32 位 `time_t` 的版本。 有关详细信息，请参阅[标准类型](../c-runtime-library/standard-types.md)以及文档中对各时间函数的注释。  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)