---
title: "strftime、wcsftime、_strftime_l、_wcsftime_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strftime"
  - "_wcsftime_l"
  - "_strftime_l"
  - "wcsftime"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcsftime"
  - "strftime"
  - "wcsftime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strftime_l 函数"
  - "strftime 函数"
  - "tcsftime 函数"
  - "_wcsftime_l 函数"
  - "wcsftime 函数"
  - "_tcsftime 函数"
  - "时间字符串"
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# strftime、wcsftime、_strftime_l、_wcsftime_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

格式化一个时间字符串。  
  
## 语法  
  
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
  
#### 参数  
 `strDest`  
 输出字符串  
  
 `maxsize`  
 `strDest` 缓冲区的大小，以字符测量 \(`char` 或 `wchart_t`\)。  
  
 `format`  
 窗体控件字符串。  
  
 `timeptr`  
 `tm` 数据结构  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `strftime` 返回 `strDest` 中的字符数，并且 `wcsftime` 返回相应的宽字符数。  
  
 如果字符的总数，包括空终止符，大于 `maxsize`，`strftime` 和 `wcsftime` 都返回 0，并且`strDest` 内容是不确定的。  
  
 在 `strDest` 的字符数与在 `format` 的文本字符数相等，而且任意字符可能通过格式代码添加到 `format` 中。  在返回值中不计字符串的空终止符。  
  
## 备注  
 `strftime` 和 `wcsftime` 函数根据提供的 `format` 参数格式化 `timeptr` 中 `tm` 时间值并结果存储在缓冲区 `strDest` *。*通常，`maxsize` 字符被放置在字符串中。  有关 `timeptr` 结构的字段描述，请参阅 [asctime](../../c-runtime-library/reference/asctime-wasctime.md)。  `wcsftime` 是 `strftime` 的宽字符等价物；它的字符指针参数指向宽字符字符串。  否则这些函数具有相同行为。  
  
> [!NOTE]
>  在 Visual C\+\+ 2005 之前的版本，该文档描述了 `wcsftime` 的 `format` 参数具有 `const wchar_t *`数据类型，但是`format` 数据类型的实际实现是 `const char *`。  `format`数据类型实现已经更新以反映以前和当前文档，正如 `const wchar_t *`。  
  
 此函数验证其参数。  如果 `strDest`、`format`或`timeptr` 为空指针，或如果通过 `timeptr` 定义的 `tm` 数据结构是无效的 \(例如，如果它包含不在时间或日期范围的值\)，或者如果 `format` 字符串包含一个无效的格式代码，则调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则该函数返回 0 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 `format` 参数包含一个或多个代码；正如在 `printf`中，格式代码在百分号 \(`%`\) 之后。  不以 `%` 开头的字符将不改变地复制到 `strDest`*。*当前区域设置的 `LC_TIME` 类别会影响 `strftime` 的输出格式。\(有关`LC_TIME`的详细信息, 请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。\)没有 `_l` 后缀的函数使用当前设置的区域设置。  这些带有 `_l` 后缀的函数的版本相同，除了它们将区域而不是当前线程区域设置视为参数并使用。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `strftime` 的格式代码如下列出：  
  
 `%a`  
 缩写的星期名称  
  
 `%A`  
 完整星期名称  
  
 `%b`  
 缩写的月份名称  
  
 `%B`  
 完整的月份名称。  
  
 `%c`  
 日期和时间表示恰当的区域设置  
  
 `%d`  
 日期为十进制数字 \(01 \- 31\) 的月份  
  
 `%H`  
 以 24 小时格式 \(00 \- 23\) 的点  
  
 `%I`  
 以 12 小时格式 \(01 \- 12\) 的点  
  
 `%j`  
 日期为十进制数字 \(001 \- 366\)。  
  
 `%m`  
 为十进制数字 \(01 \- 12\) 的月份  
  
 `%M`  
 为十进制数字 \(00 \- 59\) 的分钟  
  
 `%p`  
 12 小时时钟的当前区域设置的 A.M\/P.M. 指示器  
  
 `%S`  
 其次为十进制数字 \(00 \- 59\)  
  
 `%U`  
 周为十进制数字的年份，周日为一周的第一天 \(00 \- 53\)  
  
 `%w`  
 周为十进制数字 \(0 \- 6 ；0 是星期天\)  
  
 `%W`  
 周为十进制数字的年份，星期一为一周的第一天 \(00 \- 53\)  
  
 `%x`  
 当前区域设置的日期显示  
  
 `%X`  
 当前区域设置的时间显示  
  
 `%y`  
 无世纪年，为十进制数字 \(00 \- 99\)  
  
 `%Y`  
 世纪年，为十进制数字  
  
 `%z, %Z`  
 根据注册表设置，无论是时区名称或时区缩写，如果时区未知，则没有字符  
  
 `%%`  
 百分号  
  
 在 `printf` 函数中，`#` 标志将格式化所有代码前缀。  在这种情况下，格式代码的含义如下改变。  
  
|格式代码|含义|  
|----------|--------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|`#` 标志被忽略。|  
|`%#c`|完整日期和时间表示法适于当前区域设置。  例如：“星期二，1995 年 3 月 14 日 12:41:29 " 。|  
|`%#x`|完整日期表示法适于当前区域设置。  例如：“星期二，1995 年 3 月 14 日 " 。|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|删除前导零 \(如果有\)。|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strftime`|\<time.h\>|  
|`wcsftime`|\<time.h\> or \<wchar.h\>|  
|`_strftime_l`|\<time.h\>|  
|`_wcsftime_l`|\<time.h\> or \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [time](../../c-runtime-library/reference/time-time32-time64.md) 的示例。  
  
## .NET Framework 等效项  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [时间管理](../../c-runtime-library/time-management.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)