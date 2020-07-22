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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 57fdd61a966cbeab07c0aeafdad0f6e6fb97cca1
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404315"
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

*strDest*<br/>
输出字符串。

*maxsize*<br/>
*StrDest*缓冲区的大小（以字符（**char**或**wchar_t**）为单位）。

*format*<br/>
窗体控件字符串。

*timeptr*<br/>
**tm**数据结构。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strftime**返回*strDest*和**wcsftime**中放置的字符数返回相应的宽字符数。

如果字符总数（包括终止 null）大于*maxsize*，则**strftime**和**Wcsftime**都返回0， *strDest*的内容不确定。

*StrDest*中的字符数等于*格式*中的文本字符数，以及可以通过格式设置代码添加到*格式*的任何字符。 返回值中一般不计算以 null 终止的字符串。

## <a name="remarks"></a>备注

**Strftime**和**wcsftime**函数根据提供的*格式*参数格式化*timeptr*中的**tm** time 值，并将结果存储在缓冲区*strDest*中。 最多可以在字符串中放置*maxsize*字符。 有关*timeptr*结构中的字段的说明，请参阅[asctime](asctime-wasctime.md)。 **wcsftime**是**strftime**的宽字符等效项;其字符串指针参数指向宽字符字符串。 否则这些函数具有相同行为。

此函数验证其参数。 如果*strDest*、 *format*或*timeptr*为 null 指针，或者如果*timeptr*解决的**tm**数据结构无效（例如，如果它包含的时间或日期范围外的值），或者如果*格式*字符串包含无效的格式设置代码，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回0并将**errno**设置为**EINVAL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*Format*参数包含一个或多个代码;与**printf**中一样，格式设置代码前面有一个百分号（ **%** ）。 不以开头的字符 **%** 将复制到*strDest*中。 当前区域设置的**LC_TIME**类别将影响**strftime**的输出格式。 （有关**LC_TIME**的详细信息，请参阅[setlocale](setlocale-wsetlocale.md)。）**Strftime**和**wcsftime**函数使用当前设置的区域设置。 这些函数的 **_strftime_l**和 **_wcsftime_l**版本相同，只不过它们将区域设置用作参数并使用它，而不是使用当前设置的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**Strftime**函数支持以下格式代码：

|||
|-|-|
|代码|替换字符串|
|**% a**|区域设置中缩写的星期几名称|
|**% A**|区域设置中的完整星期几名称|
|**% b**|区域设置中缩写的月份名称|
|**% B**|区域设置中的完整月份名称|
|**% c**|适用于区域设置的日期和时间表示|
|**% C**|年除以100并截断为整数，作为十进制数（00−99）|
|**% d**|以十进制数字表示的月中的某一日（01-31）|
|**% D**|等效于 **% m/% d/% y**|
|**% e**|以十进制数字表示的月中的某一日（1-31），其中单个数字前面有一个空格|
|**% F**|等效于 **% Y-% m-% d**|
|**% g**|ISO 8601 基于周的年份的最后两位数字（00-99）|
|**% G**|ISO 8601 基于周的年份作为小数|
|**% h**|缩写月份名称（等同于 **% b**）|
|**% H**|24小时制的小时（00-23）|
|**% I**|12小时制的小时（01-12）|
|**% j**|以十进制数字表示的一年中的第几天（001-366）|
|**% m**|以十进制数字表示的月份（01-12）|
|**% M**|以十进制数字表示的分钟数（00-59）|
|**% n**|换行符（**\n**）|
|**% p**|区域设置的 A.M./P.M。 A.M./P.M. 指示器|
|**% r**|区域设置的12小时制时间|
|**% R**|等效于 **% H:%M**|
|**% S**|秒作为小数（00-59）|
|**% t**|水平制表符（**\t**）|
|**% T**|等效于 **% H:%M：% S**，ISO 8601 时间格式|
|**% u**|ISO 8601 工作日作为小数（1-7;星期一为1）|
|**% U**|以十进制数字表示的年周数（00-53），其中第一个星期日是第1周的第一天|
|**% V**|ISO 8601 周号码作为小数（00-53）|
|**% w**|以十进制数字表示的工作日（0-6;星期日为0）|
|**% W**|以十进制数字表示的年周数（00-53），其中第一个星期一是第1周的第一天|
|**% x**|区域设置的日期表示形式|
|**% X**|区域设置的时间表示形式|
|**% y**|不带世纪的年份，十进制数字（00-99）|
|**% Y**|以十进制数字表示的带有世纪数的年份|
|**% z**|以 ISO 8601 格式形式相对于 UTC 的偏移量;如果时区未知，则没有字符|
|**% Z**|区域设置的时区名称或时区缩写（取决于注册表设置）;如果时区未知，则没有字符|
|**%%**|百分号|

与**printf**函数一样， **#** 标志可以为任何格式设置代码加前缀。 在这种情况下，格式代码的含义更改为如下内容。

|格式代码|含义|
|-----------------|-------------|
|**% #a**， **% #A**， **% #b**， **% #B**， **% #g**， **% #G**， **% #h**， **% #n**， **% #p**， **% #t**， **% #u**， **% #w**， **% #X**， **% #z**， **% #Z**，**%#%**|**#** 已忽略标志。|
|**% #c**|适用于区域设置的长日期和时间表示形式。 例如：“1995 年 3 月 14 日，星期二，12:41:29”。|
|**% #x**|适用于区域设置的长日期表示形式。 例如：“1995 年 3 月 14 日，星期二”。|
|**% #d**， **% #D**， **% #e**， **% #F**， **% #H**， **% #I**， **% #j**， **% #m**， **% #M**， **%** **#r，% #R，**% **#S**， **%**#T， **% #U**，% **#V**， **% #W**， **% #y**， **% #Y**|删除前导零或空格（如果有）。|

**% V**、 **% g**和 **% g**生成的基于 ISO 8601 周和每周的年份使用的周始于星期一，其中第1周是包含一年中至少四天的第一周。 如果该年的第一个星期一为第二个、第三个或第四个星期，则前一年的最后一周是第一天。 对于这些天， **% V**被替换为53，而 **% g**和 **% g**均替换为上一年的位数。

> [!NOTE]
> 将其中一个 `strftime` 函数与从返回的指针一起使用时 `tm` `gmtime` ，通过和说明符打印的值 `%Z` `%z` 将不准确。 这是因为 `tm` C 标准指定的结构不包含时区名称的信息，也不包含偏移量的信息。 而是通过全局变量[ `_timezone` 和 `_dstbias` ](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)填充时区信息。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> 或 \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> 或 \<wchar.h>|

**_Strftime_l**和 **_Wcsftime_l**函数是 Microsoft 特定的。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [time](time-time32-time64.md) 的示例。

## <a name="see-also"></a>另请参阅

[区域设置](../../c-runtime-library/locale.md) <br/>
[时间管理](../../c-runtime-library/time-management.md) <br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
