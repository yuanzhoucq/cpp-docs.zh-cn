---
title: "vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vfwprintf_s"
  - "_vfprintf_s_l"
  - "vfprintf_s"
  - "_vfwprintf_s_l"
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
apitype: "DLLExport"
f1_keywords: 
  - "_vftprintf_s"
  - "vfwprintf_s"
  - "vfprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vfprintf_s_l 函数"
  - "_vftprintf_s 函数"
  - "_vftprintf_s_l 函数"
  - "_vfwprintf_s_l 函数"
  - "格式化文本 [C++]"
  - "vfprintf_s 函数"
  - "vfprintf_s_l 函数"
  - "vftprintf_s_l 函数"
  - "vfwprintf_s 函数"
  - "vfwprintf_s_l 函数"
ms.assetid: eab6f563-46e2-4806-963f-2b23f339ecdc
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编写使用指针参数列表的格式化输出。  [vfprintf、\_vfprintf\_l、vfwprintf、\_vfwprintf\_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
int vfprintf_s(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_s_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vfwprintf_s(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_s_l(  
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 如果输出有错误，`vfprintf_s`和 `vfwprintf_s`返回编写的字符数，不包括终止空字符或负值。  如果 `stream`或`format` 是空指针，或者，如果格式字符串包含无效格式字符，无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个函数通过指针指向参数列表，然后布局和编写特定数据到`stream`。  
  
 这些函数与安全版本 的不同之处仅在于安全版本检查包含有效格式字符的`format`字符串。  
  
 `vfwprintf_s` 是 `vfprintf_s`的宽字符版本；如果流在 ANSI 模式下是公开的则两个函数具有相同行为。  `vfprintf_s` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_vftprintf_s`|`vfprintf_s`|`vfprintf_s`|`vfwprintf_s`|  
|`_vftprintf_s_l`|`_vfprintf_s_l`|`_vfprintf_s_l`|`_vfwprintf_s_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`vfprintf_s`, \_`vfprintf_s_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`vfwprintf_s`, \_`vfwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)