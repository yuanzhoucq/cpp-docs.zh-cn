---
title: strftime、wcsftime、_strftime_l、_wcsftime_l
ms.date: 03/22/2018
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
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 932a7827ef61a5e111f86f8bc44291827843b76e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505659"
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
大小*strDest*缓冲区，以字符为单位 (**char**或**wchar_t**)。

*format*<br/>
窗体控件字符串。

*timeptr*<br/>
**tm**数据结构。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strftime**返回的字符放入数*strDest*并**wcsftime**返回相应的宽字符数。

如果字符，包括终止 null，总数为多个*maxsize*，这两个**strftime**并**wcsftime**返回 0，并且的内容*strDest*是不确定的。

中的字符数*strDest*等同于中的原义字符数目*格式*以及可能会添加到任何字符*格式*通过格式化代码。 返回值中一般不计算以 null 终止的字符串。

## <a name="remarks"></a>备注

**Strftime**并**wcsftime**函数格式**tm**时间值中的*timeptr*根据所提供*格式*自变量并在缓冲区中将结果存储*strDest*。 最多*maxsize*字符放置在字符串中。 有关中的字段的说明*timeptr*结构，请参阅[asctime](asctime-wasctime.md)。 **wcsftime**相当于宽字符**strftime**; 其字符串指针参数指向宽字符字符串。 否则这些函数具有相同行为。

此函数验证其参数。 如果*strDest*，*格式*，或*timeptr*是 null 指针，或者如果**tm**数据结构所处理的*timeptr*无效 （例如，如果它包含的时间或日期超出范围的值），或者如果*格式*字符串包含无效的格式化代码，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回 0 并设置**errno**到**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*格式*自变量包含的一个或多个代码; 如下所示**printf**，格式化代码前面带有百分号 (**%**)。 不以开头的字符**%** 原样复制到*strDest*。 **LC_TIME**类别的当前区域设置影响的输出格式**strftime**。 (有关详细信息**LC_TIME**，请参阅[setlocale](setlocale-wsetlocale.md)。)**Strftime**并**wcsftime**函数使用当前设置的区域设置。 **_Strftime_l**并 **_wcsftime_l**这些函数的版本完全相同，只不过它们将区域设置用作参数并使用它而不是当前设置的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函数支持这些格式设置代码：

|||
|-|-|
|代码|替换字符串|
|**%a**|区域设置中的缩写的星期几名称|
|**%A**|区域设置中的完整的星期几名称|
|**%b**|区域设置中的缩写的月份名称|
|**%B**|区域设置中的完整的月份名称|
|**%c**|适用于区域设置的日期和时间表示|
|**%C**|年除以 100 并截断为整数，以十进制数 (00−99)|
|**%d**|以十进制数 (01-31) 的每月天数|
|**%D**|等效于 **%m/%d/%y**|
|**%e**|为其中的一位数字的前面有一个空格的十进制数字 (1-31)，每月天数|
|**%F**|等效于 **%y-%m-%d**|
|**%g**|以十进制数的 ISO 8601 周基于年份的最后 2 个数字 (00-99)|
|**%G**|ISO 8601 周基于年以十进制数|
|**%h**|缩写的月份名称 (等效于 **%b**)|
|**%H**|24 小时制的小时 (00-23)|
|**%I**|小时采用 12 小时格式 （01 到 12 个）|
|**%j**|以十进制数 (001-366) 年的某一天|
|**%m**|以十进制数 (01-12) 个月|
|**%M**|以十进制数分钟 (00-59)|
|**%n**|换行字符 (**\n**)|
|**%p**|区域设置的 a.m./p.m.。 12 小时制的指示器|
|**%r**|区域设置的 12 小时时钟时间|
|**%R**|等效于 **%H:%M**|
|**%S**|以十进制数第二个 (00-59)|
|**%t**|水平制表符 (**\t**)|
|**%T**|等效于 **%h:%m:%s**，ISO 8601 时间格式|
|**%u**|以十进制数 (1-7; ISO 8601 星期几星期一为 1）|
|**%U**|十进制数字表示年份的周数 (00-53)，其中第一个星期日是第 1 周的第一天|
|**%V**|以十进制数的 ISO 8601 周数 (00-53)|
|**%w**|以十进制数的工作日 (0-6;星期日为 0）|
|**%W**|十进制数字表示年份的周数 (00-53)，其中第一个星期一是第 1 周的第一天|
|**%x**|区域设置的日期表示形式|
|**%X**|区域设置的时间表示形式|
|**%y**|不带世纪数位，以十进制数字的年份 (00-99)|
|**%Y**|以十进制数字表示的带有世纪数的年份|
|**%z**|从 UTC 的偏移量，采用 ISO 8601 格式;如果时区未知，则没有字符|
|**%Z**|区域设置的时区名称或时区缩写，具体取决于注册表设置;如果时区未知，则没有字符|
|**%%**|百分号|

在中作为**printf**函数， **#** 标志可能前缀格式设置的任何代码。 在这种情况下，格式代码的含义更改为如下内容。

|格式代码|含义|
|-----------------|-------------|
|**%#a**， **%#A**， **%#b**， **%#B**， **%#g**， **%#G**， **%#h**， **%#n**， **%#p**， **%#t**， **%#u**， **%#w**， **%#X**， **%#z**， **%#Z**， **%#%**|**#** 将忽略标志。|
|**%#c**|长日期和时间表示形式，适用于区域设置。 例如：“1995 年 3 月 14 日，星期二，12:41:29”。|
|**%#x**|长日期表示形式，适合于区域设置。 例如：“1995 年 3 月 14 日，星期二”。|
|**%#d**， **%#D**， **%#e**， **%#F**， **%#H**， **%#I**， **%#j**， **%#m**， **%#M**， **%#r**， **%#R**， **%#S**， **%#T**， **%#U**， **%#V**， **%#W**， **%#y**， **%#Y**|删除前导零或空格 （如果有）。|

由生成的 ISO 8601 周和每周基于年份 **%V**， **%g**，并 **%G**，使用第 1 周其中是包含年 1 月第 4 个，它是第一周从星期一，开始一周包括一年中的至少包含四天的周。 如果年份的第一个星期一，第二个月 3 日或第四上, 一天是上一年的最后一周的一部分。 这些天 **%V**替换为 53，并且这两种 **%g**和 **%G**替换为上一年的某一位数字。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**并 **_wcsftime_l**函数是特定于 Microsoft 的。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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
