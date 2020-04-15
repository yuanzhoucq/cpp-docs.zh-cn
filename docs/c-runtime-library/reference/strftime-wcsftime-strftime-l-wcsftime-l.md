---
title: strftime、wcsftime、_strftime_l、_wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350007"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime、wcsftime、_strftime_l、_wcsftime_l

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

*斯特德斯特*<br/>
输出字符串。

*最大大小*<br/>
*最串D*缓冲区的大小，以字符（**字符**或**wchar_t）** 度量。

*格式*<br/>
窗体控件字符串。

*timeptr*<br/>
**tm**数据结构。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strftime**返回放置在*strD*中的字符数 **，wcsftime**返回相应的宽字符数。

如果字符总数（包括终止 null）大于*最大大小*，**则稳定时间和** **wcsftime**返回 0 和*strDest 的内容*都是不确定的。

*strDest*中的字符数等于*格式*中的字面字符数，以及可通过格式代码添加到*格式*的任何字符数。 返回值中一般不计算以 null 终止的字符串。

## <a name="remarks"></a>备注

**strftime**和**wcsftime**函数根据提供的*格式*参数格式化*时间百分*值，并将结果存储在缓冲区*strDest 中*。 **tm** 最多时 *，最大大小*字符放置在字符串中。 有关*时间点*结构中的字段的说明，请参阅[asctime](asctime-wasctime.md)。 **wcsftime**是宽字符等效于**时间;** 其字符串指针参数指向宽字符字符串。 否则这些函数具有相同行为。

此函数验证其参数。 如果*strDest、**格式*或*timeptr*是空指针，或者如果*timeptr*解决**的 tm**数据结构无效（例如，如果它包含时间或日期的出距范围值），或者如果*格式*字符串包含无效的格式代码，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回 0 并将**errno**设置到**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**斯特夫时间**|**斯特夫时间**|**wcsftime**|

*格式*参数由一个或多个代码组成;如**在 printf**中，格式代码前面有百分号**%**（）。 不开头**%** 的字符将复制到*stD。* 当前区域设置的**LC_TIME**类别会影响**稳点时间的**输出格式。 （有关**LC_TIME**的详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)。）**定时**和**wcsftime**函数使用当前设置区域设置。 这些函数**的_strftime_l**和 **_wcsftime_l**版本相同，只是它们将区域设置作为参数并使用该参数而不是当前设置的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**稳时**函数支持以下格式代码：

|||
|-|-|
|代码|替换字符串|
|**%a**|区域设置中的缩写工作日名称|
|**%A**|区域设置中的完整工作日名称|
|**%b**|区域设置中的缩写月份名称|
|**%B**|区域设置中的完整月名称|
|**%c**|适用于区域设置的日期和时间表示|
|**%C**|年份除以 100，并截断为整数，作为小数 （00+99）|
|**%d**|每月的天数为小数 （01 - 31）|
|**%D**|等效于 **%m/%d/%y**|
|**%e**|每月的一天作为小数（1 - 31），其中位数字前面有空格|
|**%F**|等效于 **%Y-%m-%d**|
|**%g**|ISO 8601 基于周的年份的最后 2 位数字为小数 （00 - 99）|
|**%G**|ISO 8601 基于周的年份作为小数|
|**%h**|缩写月份名称（等效于 **%b）**|
|**%H**|24 小时格式的小时（00 - 23）|
|**%I**|12 小时格式的小时 （01 - 12）|
|**%j**|一年中的某一天作为小数 （001 - 366）|
|**%m**|作为小数数的月份 （01 - 12）|
|**%M**|分钟作为小数 （00 - 59）|
|**%n**|新线字符 （**\n**）|
|**%p**|区域设置的 A.M./P.M. A.M./P.M. 指示器|
|**%r**|区域设置的 12 小时时钟时间|
|**%R**|等效于 **%H：%M**|
|**%S**|第二位为小数 （00 - 59）|
|**%t**|水平选项卡字符 （**\t**）|
|**%T**|等效于 **%H：%M：%S，ISO**8601 时间格式|
|**%u**|ISO 8601 工作日作为小数（1 - 7;星期一是 1）|
|**%U**|年份的周数为小数（00 - 53），其中第一个星期日是第 1 周的第一天|
|**%V**|ISO 8601 周数作为小数 （00 - 53）|
|**%w**|工作日作为小数（0 - 6;周日是 0）|
|**%W**|年份的周数为小数（00 - 53），其中第一个星期一是第 1 周的第一天|
|**%x**|区域设置的日期表示|
|**%X**|区域设置的时间表示|
|**%y**|无世纪年份，作为十进制数字 （00 - 99）|
|**%Y**|以十进制数字表示的带有世纪数的年份|
|**%z**|ISO 8601 格式的 UTC 偏移量;如果时区未知，则没有字符|
|**%Z**|区域设置的时区名称或时区缩写，具体取决于注册表设置;如果时区未知，则没有字符|
|**%%**|百分号|

与**printf**函数中一**#** 样，标志可以对任何格式代码进行前缀。 在这种情况下，格式代码的含义更改为如下内容。

|格式代码|含义|
|-----------------|-------------|
|**%#a，** **%#A**， **%#b**， **%#B**， **%#g**% **#G**% **#h**， **%#n**， **%#p**，**百分之#t**、**百分之#u**、 **%#w**、 **#X**% **#z**、**百分之#Z**、**%#%**|**#** 将忽略标志。|
|**%#c**|长日期和时间表示形式，适合区域设置。 例如：“1995 年 3 月 14 日，星期二，12:41:29”。|
|**%#x**|长日期表示形式，适合区域设置。 例如：“1995 年 3 月 14 日，星期二”。|
|**百#d**、 **#D %** **#e**、 **%#F**、 **#H**% **#I**、 **%#j**、 **#m** **%**#M 、 **#r**% **#R**、 **%#S**、 **%#T**、 **#U**、**百#V**、 **#W**% #W 、 **%#y**、 **%#Y**|删除前导零或空格（如果有）。|

由 **%V、%g**和 **%G**生产的 ISO **%g**8601 周和基于一周的年份使用从星期一开始的一周，其中第 1 周是包含 1 月 4 日的一周，即包含一年中至少四天的第一周。 如果一年的第一个星期一是第 2、3 或第 4 个，则前几天是上一年最后一周的一部分。 在那些日子里 **，%V**替换为 53，%g 和 **%G**都替换为上一年的数字。 **%g**

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**斯特夫时间**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_strftime_l**和 **_wcsftime_l**功能特定于 Microsoft。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [time](time-time32-time64.md) 的示例。

## <a name="see-also"></a>另请参阅

[现场](../../c-runtime-library/locale.md) <br/>
[时间管理](../../c-runtime-library/time-management.md) <br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
