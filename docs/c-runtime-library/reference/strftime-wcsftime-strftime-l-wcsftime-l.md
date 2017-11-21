---
title: "strftime、wcsftime、_strftime_l、_wcsftime_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec9c46f1a6d52a8769e5db454d44baf9ec9d8a8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime、wcsftime、_strftime_l、_wcsftime_l
格式化时间字符串。  
  
## <a name="syntax"></a>语法  
  
```  
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
  
#### <a name="parameters"></a>参数  
 `strDest`  
 输出字符串。  
  
 `maxsize`  
 `strDest` 缓冲区的大小，以字符（`char` 或 `wchart_t`）为单位。  
  
 `format`  
 窗体控件字符串。  
  
 `timeptr`  
 `tm` 数据结构。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `strftime` 返回置于 `strDest` 中的字符数，`wcsftime` 返回相应的宽字符数。  
  
 如果包括以 null 终止的字符在内的字符总数大于 `maxsize`，则 `strftime` 和 `wcsftime` 都将返回 0，并且 `strDest` 的内容是不确定的。  
  
 `strDest` 中的字符数等于 `format` 中的文本字符和可通过格式化代码添加到 `format` 的任何字符的数量。 返回值中一般不计算以 null 终止的字符串。  
  
## <a name="remarks"></a>备注  
 `strftime`和`wcsftime`函数格式`tm`时间中的值`timeptr`根据所提供`format`自变量和存储在缓冲区中的结果`strDest`。 该字符串最多可放置 `maxsize` 个字符。 有关 `timeptr` 结构中字段的说明，请参阅 [asctime](../../c-runtime-library/reference/asctime-wasctime.md)。 `wcsftime` 是等同于 `strftime` 的宽字符；它的字符串指针参数指向宽字符字符串。 否则这些函数具有相同行为。  
  
> [!NOTE]
>  在 Visual C ++ 2005 之前的版本中，文档将 `wcsftime` 的 `format` 参数描述为 `const wchar_t *` 数据类型，但 `format` 数据类型的实际实现是 `const char *`。 实现`format`数据类型已更新以反映的先前和当前文档，即`const wchar_t *`。  
  
 此函数验证其参数。 如果`strDest`， `format`，或`timeptr`是 null 指针，或如果`tm`数据结构由`timeptr`无效 （例如，如果它包含超出范围值的时间或日期），或者如果`format`字符串包含无效的格式设置代码，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则该函数将返回 0 并将 `errno` 设置为 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 `format` 参数由一个或多个代码组成；比如在 `printf` 中，格式化代码前面带有百分号 (`%`)。 不以开头的字符`%`复制不变以`strDest`。 当前区域设置的 `LC_TIME` 分类会影响 `strftime` 的输出格式。 （有关 `LC_TIME` 的详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)）。没有 `_l` 后缀的函数使用当前设置的区域设置。 这些带有 `_l` 后缀的函数的版本相同，只不过它们将区域设置用作参数并使用它，而不是使用当前设置的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `strftime` 的格式化代码如下所示：  
  
 `%a`  
 缩写的工作日名称  
  
 `%A`  
 完整的工作日名称  
  
 `%b`  
 缩写的月份名称  
  
 `%B`  
 完整的月份名称  
  
 `%c`  
 适用于区域设置的日期和时间表示  
  
 `%d`  
 一天的月份，十进制数字 (01 到 31)  
  
 `%H`  
 小时，24 小时制 (00-23)  
  
 `%I`  
 小时采用 12 小时格式 (01 到 12)  
  
 `%j`  
 一天的年份，十进制数字 (001-366)  
  
 `%m`  
 月份，十进制数字 (01 到 12)  
  
 `%M`  
 分钟，十进制数字 (00-59)  
  
 `%p`  
 12 小时制的当前区域设置的  A.M./P.M. 指示器  
  
 `%S`  
 第二个十进制数字 (00-59)  
  
 `%U`  
 年的十进制数，星期日是一周中的第一天的周 (00-53)  
  
 `%w`  
 星期，十进制数字 (0-6;星期日为 0）  
  
 `%W`  
 周的年份，十进制数字，星期一是一周中的第一天 (00-53)  
  
 `%x`  
 当前区域设置的日期表示形式  
  
 `%X`  
 当前区域设置的时间表示形式  
  
 `%y`  
 不带世纪，十进制数字的年份 (00-99)  
  
 `%Y`  
 以十进制数字表示的带有世纪数的年份  
  
 `%z, %Z`  
 时区名称或时区缩写取决于注册表设置；如果时区未知，则没有字符  
  
 `%%`  
 百分号  
  
 与在 `printf` 函数中一样，`#` 标志可以成为任何格式化代码前缀。 在这种情况下，格式代码的含义更改为如下内容。  
  
|格式代码|含义|  
|-----------------|-------------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|忽略 `#` 标志。|  
|`%#c`|长的日期和时间表示形式，适用于当前区域设置。 例如：“1995 年 3 月 14 日，星期二，12:41:29”。|  
|`%#x`|长的日期表示形式，适用于当前区域设置。 例如：“1995 年 3 月 14 日，星期二”。|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|请删除前导零（如果存在）。|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`strftime`|\<time.h>|  
|`wcsftime`|\<time.h> 或 \<wchar.h>|  
|`_strftime_l`|\<time.h>|  
|`_wcsftime_l`|\<time.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [time](../../c-runtime-library/reference/time-time32-time64.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [时间管理](../../c-runtime-library/time-management.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)