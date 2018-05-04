---
title: strftime、wcsftime、_strftime_l、_wcsftime_l | Microsoft 文档
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 573e89b7be9818ac45f70c7c614e3bf7869c95f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime、wcsftime、_strftime_l、_wcsftime_l

格式化时间字符串。

## <a name="syntax"></a>语法

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strDest*<br/>
输出字符串。

*最大大小*<br/>
大小*strDest*缓冲区，以字符为单位测量 (**char**或**wchar_t**)。

*format*<br/>
窗体控件字符串。

*timeptr*<br/>
**tm**数据结构。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strftime**返回数目的字符放入*strDest*和**wcsftime**返回相应的宽字符数。

如果个字符，包括终止 null 的总数为多个*maxsize*，这两个**strftime**和**wcsftime**返回 0 和内容*strDest*是不确定的。

中的字符数*strDest*等于文本中的字符数*格式*以及可能添加到任何字符*格式*通过格式设置代码。 返回值中一般不计算以 null 终止的字符串。

## <a name="remarks"></a>备注

**Strftime**和**wcsftime**函数格式**tm**时间中的值*timeptr*根据所提供*格式*自变量和存储在缓冲区中的结果*strDest*。 最多， *maxsize*在字符串中放置的字符。 有关中的字段的说明*timeptr*结构，请参阅[asctime](asctime-wasctime.md)。 **wcsftime**相当于宽字符**strftime**; 其字符串指针自变量指向的宽字符字符串。 否则这些函数具有相同行为。

此函数验证其参数。 如果*strDest*，*格式*，或*timeptr*是 null 指针，或如果**tm**数据结构由*timeptr*无效 （例如，如果它包含超出范围值的时间或日期），或者如果*格式*字符串包含无效的格式设置代码，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回 0 并设置**errno**到**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*格式*自变量包含一个或多个代码; 如下所示**printf**，格式设置代码的前面一个百分号 (**%**)。 不以开头的字符**%** 复制不变以*strDest*。 **LC_TIME**当前区域设置类别的影响的输出格式**strftime**。 (有关详细信息**LC_TIME**，请参阅[setlocale](setlocale-wsetlocale.md)。)**Strftime**和**wcsftime**函数使用当前设置区域设置。 **_Strftime_l**和 **_wcsftime_l**这些函数的版本都相同，只不过它们需要作为参数的区域设置和使用，而不是当前设置区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函数支持这些格式设置代码：

|||
|-|-|
|代码|替换字符串|
|**%a**|区域设置中的缩写的星期几名称|
|**%A**|区域设置中的完整的星期几名称|
|**%b**|区域设置中的月份的缩写的名称|
|**%B**|区域设置中的完整的月份名称|
|**%c**|适用于区域设置的日期和时间表示|
|**%C**|年除以 100 并截断为整数、 十进制数字 (00−99)|
|**%d**|一天的月份，十进制数字 (01 到 31)|
|**%D**|等效于 **%m/%d/%y**|
|**%e**|为单个数字前加一个空格的其中一个十进制数 (1-31)，每月天数|
|**%F**|等效于 **%y-%m-%d**|
|**%g**|ISO 8601 基于周的年份，十进制数字最后 2 数字 (00-99)|
|**%G**|ISO 8601 基于周的年份，十进制数字|
|**%h**|月份的缩写的名称 (等效于 **%b**)|
|**%H**|小时，24 小时制 (00-23)|
|**%I**|小时采用 12 小时格式 (01 到 12)|
|**%j**|十进制数字 (001-366) 年的某一天|
|**%m**|月份，十进制数字 (01 到 12)|
|**%M**|分钟，十进制数字 (00-59)|
|**%n**|换行符 (**\n**)|
|**%p**|区域设置的 a.m./p.m.。 A.M./P.M. 指示器|
|**%r**|区域设置的 12 小时时钟制时间|
|**%R**|等效于 **%h%M:**|
|**%S**|第二个十进制数字 (00-59)|
|**%t**|水平制表符 (**\t**)|
|**%T**|等效于 **%h: %m%S:**，ISO 8601 时间格式|
|**%u**|ISO 8601 星期，十进制数字 (1-7;星期一为 1）|
|**%U**|周数的十进制数表示的年份 (00-53)，其中的第一个星期日是第 1 周的第一天|
|**%V**|ISO 8601 周数为十进制数字 (00-53)|
|**%w**|星期，十进制数字 (0-6;星期日为 0）|
|**%W**|周数的十进制数表示的年份 (00-53)，其中的第一个星期一是第 1 周的第一天|
|**%x**|区域设置的日期表示形式|
|**%X**|区域设置的时间表示形式|
|**%y**|不带世纪，十进制数字的年份 (00-99)|
|**%Y**|以十进制数字表示的带有世纪数的年份|
|**%z**|从 UTC 的偏移量，采用 ISO 8601 格式;如果时区未知的任何字符|
|**%Z**|区域设置的时区名称或时区缩写，具体取决于注册表设置;如果时区未知的任何字符|
|**%%**|百分号|

作为 in **printf**函数， **#** 标志可能前缀格式设置的任何代码。 在这种情况下，格式代码的含义更改为如下内容。

|格式代码|含义|
|-----------------|-------------|
|**%#a**， **%#A**， **%#b**， **%#B**， **%#g**， **%#G**， **%#h**， **%#n**， **%#p**， **%#t**， **%#u**， **%#w**， **%#X**， **%#z**， **%#Z**， **%#%**|**#** 将忽略标志。|
|**%#c**|长日期和时间表示形式，适用于区域设置。 例如：“1995 年 3 月 14 日，星期二，12:41:29”。|
|**%#x**|长日期表示形式，适合于区域设置。 例如：“1995 年 3 月 14 日，星期二”。|
|**%#d**， **%#D**， **%#e**， **%#F**， **%#H**， **%#I**， **%#j**， **%#m**， **%#M**， **%#r**， **%#R**， **%#S**， **%#T**， **%#U**， **%#V**， **%#W**， **%#y**， **%#Y**|删除前导零或空格 （如果有）。|

ISO 8601 每周和每周基于年份由 **%V**， **%g**，和 **%G**，使用从星期一，开始一周，第 1 周是包含年 1 月 4 日，即第一个周包含至少四天年的某一周。 如果在一年的第一个星期一，第二个月 3 日或第四个的前面日期是上一年的最后一周的一部分。 对于这些天， **%V**替换为 53，和都 **%g**和 **%G**替换为上一年的位数。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**和 **_wcsftime_l**函数是特定于 Microsoft 的。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [time](time-time32-time64.md) 的示例。

## <a name="see-also"></a>请参阅

[区域设置](../../c-runtime-library/locale.md) <br/>
[时间管理](../../c-runtime-library/time-management.md) <br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
