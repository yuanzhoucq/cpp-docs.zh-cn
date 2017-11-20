---
title: "vprintf 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: vprintf
dev_langs: C++
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a888f46912aaa5292e9bcf1f83bc3e6926f73d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="vprintf-functions"></a>vprintf 函数
每个 `vprintf` 函数均采用一个指向参数列表的指针，然后将给定数据格式化并写入到特定目标。 函数在执行参数验证过程中会有所不同，无论函数是采用宽字符字符串还是单字节字符串、是否具有输出目标以及是否支持指定格式字符串中使用的参数的顺序。  
  
|||  
|-|-|  
|[_vcprintf、_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf、_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## <a name="remarks"></a>备注  
 `vprintf` 函数类似于下表中列出的其对应函数。 但是，每个 `vprintf` 函数接受一个指向参数列表的指针，而每个对应函数都接受一个参数列表。  
  
 这些函数格式化用于输出到目标的数据，如下所示。  
  
|函数|对应函数|输出目标|参数验证|位置参数支持|  
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|  
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|控制台|检查是否为 NULL。|no|  
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|控制台|检查是否为 NULL。|no|  
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|流|检查是否为 NULL。|no|  
|vfprintf_p|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|流|检查是否为 NULL 以及格式是否有效。|是|  
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|流|检查是否为 NULL 以及格式是否有效。|no|  
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|流|检查是否为 NULL。|no|  
|vfwprintf_p|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|流|检查是否为 NULL 以及格式是否有效。|是|  
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|流|检查是否为 NULL 以及格式是否有效。|no|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|检查是否为 NULL。|no|  
|vprintf_p|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|检查是否为 NULL 以及格式是否有效。|是|  
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|检查是否为 NULL 以及格式是否有效。|no|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|检查是否为 NULL。|no|  
|vwprintf_p|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|检查是否为 NULL 以及格式是否有效。|是|  
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|检查是否为 NULL 以及格式是否有效。|no|  
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|buffer 指向的内存|检查是否为 NULL。|no|  
|vsprintf_p|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|buffer 指向的内存|检查是否为 NULL 以及格式是否有效。|是|  
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|buffer 指向的内存|检查是否为 NULL 以及格式是否有效。|no|  
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|buffer 指向的内存|检查是否为 NULL。|no|  
|vswprintf_p|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|buffer 指向的内存|检查是否为 NULL 以及格式是否有效。|是|  
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|buffer 指向的内存|检查是否为 NULL 以及格式是否有效。|no|  
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|buffer 指向的内存|检查是否为 NULL。|no|  
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|buffer 指向的内存|检查是否为 NULL。|no|  
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|buffer 指向的内存|检查是否为 NULL。|no|  
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|buffer 指向的内存|检查是否为 NULL。|no|  
  
 `argptr` 参数的类型为 `va_list`，它在 VARARGS.H 和 STDARG.H 中定义。 `argptr` 变量必须由 va_start 初始化，并可由后续的 `va_arg` 调用重新初始化；然后 `argptr` 指向根据 format 参数中的相应规范转换和传输以用于输出的参数列表的开头。 format 具有与 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 format 参数相同的形式和函数。 这些函数均不会调用 `va_end`。 有关每个 `vprintf` 函数的更完整的说明，请参阅前面表中列出的其对应函数的说明。  
  
 `_vsnprintf` 与 vsprintf 的不同之处在于，前者写入 buffer 的内容不超过 count 字节。  
  
 名称中带有 w 中缀的这些函数的版本是不带 w 中缀的相应函数的宽字符版本；在其中每个宽字符函数中，buffer 和 format 是宽字符字符串。 否则，每个宽字符函数的行为会与其 SBCS 对应函数相同。  
  
 具有 _s 和 _p 后缀的这些函数的版本是更安全的版本。 这些版本验证格式字符串，如果格式字符串格式不正确（例如，使用无效的格式化字符的情况），这些版本会生成异常。  
  
 具有 _p 后缀的这些函数的版本提供指定所提供的参数在格式字符串中替换的顺序的功能。 有关详细信息，请参阅 [printf_p 位置参数](../c-runtime-library/printf-p-positional-parameters.md)。  
  
 对于 vsprintf、`vswprintf`、`_vsnprintf` 和 `_vsnwprintf`，如果在重叠的字符串之间发生复制，则此行为不确定。  
  
> [!IMPORTANT]
>  确保 format 不是用户定义的字符串。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 如果使用这些函数的安全版本（_s 或 _p 后缀），如果用户提供的字符串包含无效的格式化字符，则用户提供的格式字符串可能会触发无效参数异常。  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../c-runtime-library/stream-i-o.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg、va_copy、va_end、va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)