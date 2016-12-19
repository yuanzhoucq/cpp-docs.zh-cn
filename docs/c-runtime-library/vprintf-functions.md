---
title: "vprintf 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "vprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "格式化文本 [C++]"
  - "vprintf 函数"
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vprintf 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个 `vprintf` 函数采用指向参数列表的指针，然后规定并写入给定数据到特定目标。  函数与参数验证执行不一样，不论函数是采用宽或单字节字符串，输出目标和用于指定参数中顺序的支持都是用于格式字符串。  
  
|||  
|-|-|  
|[\_vcprintf, \_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[\_vfprintf\_p、\_vfprintf\_p\_l、\_vfwprintf\_p、\_vfwprintf\_p\_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf\_s、\_vfprintf\_s\_l、vfwprintf\_s、\_vfwprintf\_s\_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[\_vprintf\_p、\_vprintf\_p\_l、\_vwprintf\_p、\_vwprintf\_p\_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf\_s、\_vprintf\_s\_l、vwprintf\_s、\_vwprintf\_s\_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[\_vsprintf\_p、\_vsprintf\_p\_l、\_vswprintf\_p、\_vswprintf\_p\_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf\_s、\_vsprintf\_s\_l、vswprintf\_s、\_vswprintf\_s\_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[\_vscprintf、\_vscprintf\_l、\_vscwprintf、\_vscwprintf\_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[\_vsnprintf, \_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## 备注  
 `vprintf` 函数与如下表列出的其对等函数相似。  但是，每个 `vprintf` 函数接受一个指向参数列表的指针，而每个相似函数接受一个参数列表。  
  
 这些功能格式格式数用于输出到如下目标。  
  
|功能|复制函数|输出目标|参数验证|位置参数支持|  
|--------|----------|----------|----------|------------|  
|`_vcprintf`|[\_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|控制台|空的检查。|no|  
|`_vcwprintf`|[\_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|控制台|空的检查。|no|  
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*流*|空的检查。|no|  
|**vfprintf\_p**|[fprintf\_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*流*|空和有效格式的检查。|yes|  
|`vfprintf_s`|[fprintf\_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*流*|空和有效格式的检查。|no|  
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*流*|空的检查。|no|  
|**vfwprintf\_p**|[fwprintf\_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*流*|空和有效格式的检查。|yes|  
|`vfwprintf_s`|[fwprintf\_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*流*|空和有效格式的检查。|no|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|空的检查。|no|  
|**vprintf\_p**|[printf\_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|空和有效格式的检查。|yes|  
|`vprintf_s`|[printf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|空和有效格式的检查。|no|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|空的检查。|no|  
|**vwprintf\_p**|[wprintf\_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|空和有效格式的检查。|yes|  
|`vwprintf_s`|[wprintf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|空和有效格式的检查。|no|  
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|内存通过 *缓冲区*指向|空的检查。|no|  
|**vsprintf\_p**|[sprintf\_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|内存通过 *缓冲区*指向|空和有效格式的检查。|yes|  
|`vsprintf_s`|[sprintf\_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|内存通过 *缓冲区*指向|空和有效格式的检查。|no|  
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|内存通过 *缓冲区*指向|空的检查。|no|  
|**vswprintf\_p**|[swprintf\_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|内存通过 *缓冲区*指向|空和有效格式的检查。|yes|  
|`vswprintf_s`|[swprintf\_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|内存通过 *缓冲区*指向|空和有效格式的检查。|no|  
|`_vscprintf`|[\_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|内存通过 *缓冲区*指向|空的检查。|no|  
|`_vscwprintf`|[\_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|内存通过 *缓冲区*指向|空的检查。|no|  
|`_vsnprintf`|[\_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|内存通过 *缓冲区*指向|空的检查。|no|  
|`_vsnwprintf`|[\_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|内存通过 *缓冲区*指向|空的检查。|no|  
  
 `argptr` 参数的类型为 `va_list`，在 VARARGS.H 和 STDARG.H. 定义。  `argptr` 变量必须由**va\_start,** 初始化，然后可能由后续的`va_arg` 调用重新初始化；然后 `argptr` 指向参数列表的开头，该参数用于根据 *格式* 参数对应规范的输出转换和传输。  *格式* 具有和 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)的*格式* 参数相同的窗体和函数。  这些函数没有调用 `va_end`。  有关每个 `vprintf` 函数的完整说明，请参阅上表列出的其相关函数的说明。  
  
 `_vsnprintf` 与 **vsprintf** 不同因为它不仅仅把 *计数* 字节写入到 *缓冲区*。  
  
 名称中含 **w**中缀的函数版本是没有**w**中缀的对应函数的宽字符版本；*缓冲区* 和 *格式* 是宽字符字符串。  否则，每个宽字符函数与其SBCS 对等的函数表现相同。  
  
 这些含 **\_s** 以及 **\_p** 后缀函数版本安全性更高。  这些版本验证格式字符串并将生成异常，如果格式字符串没有形成 \(例如，如果无效的格式字符被使用\)。  
  
 这些含**\_p** 后缀的函数版本提供能够指定在格式字符串中被替换的给定参数的顺序。  有关详细信息，请参阅[printf\_p 位置参数](../c-runtime-library/printf-p-positional-parameters.md)。  
  
 如果复制出现在重叠的字符串之间，对于**vsprintf**，`vswprintf`，`_vsnprintf` 和 `_vsnwprintf`，这些行为不确定。  
  
> [!IMPORTANT]
>  确保*格式*不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  如果使用这些函数的安全版本（ **\_s** 或 **\_p** 后缀），则用户提供的格式字符串可以触发无效的参数异常，如果用户提供的字符串包含无效的格式字符。  
  
## 请参阅  
 [流 I\/O](../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)