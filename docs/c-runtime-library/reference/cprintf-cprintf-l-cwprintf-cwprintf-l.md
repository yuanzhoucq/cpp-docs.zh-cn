---
title: "_cprintf、_cprintf_l、_cwprintf、_cwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cwprintf_l"
  - "_cprintf_l"
  - "_cwprintf"
  - "_cprintf"
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
  - "_cwprintf"
  - "cwprintf"
  - "tcprintf"
  - "_tcprintf"
  - "_cprintf"
  - "cwprintf_l"
  - "tcprintf_l"
  - "_tcprintf_l"
  - "cprintf_l"
  - "_cprintf_l"
  - "_cwprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cprintf 函数"
  - "_cprintf_l 函数"
  - "_cwprintf 函数"
  - "_cwprintf_l 函数"
  - "_tcprintf 函数"
  - "_tcprintf_l 函数"
  - "字符, 打印到控制台"
  - "cprintf_l 函数"
  - "cwprintf 函数"
  - "cwprintf_l 函数"
  - "将字符打印到控制台"
  - "tcprintf 函数"
  - "tcprintf_l 函数"
ms.assetid: 67ffefd4-45b3-4be0-9833-d8d26ac7c4e2
caps.latest.revision: 34
caps.handback.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cprintf、_cprintf_l、_cwprintf、_cwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

布局和输出到控件中。  更多安全版本可用；请参见 [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _cprintf(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_l(   
   const char * format,  
   locale_t locale [,  
   argument] …   
);  
int _cwprintf(  
   const wchar * format [,   
   argument] …  
);  
int _cwprintf_l(  
   const wchar * format,  
   locale_t locale [,   
   argument] …  
);  
```  
  
#### 参数  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 已打印的字符数。  
  
## 备注  
 这些 `` 功能设置格式并打印一系列字符和值直接添加到控件中，使用 `_putch` 功能 \( `_cwprintf`的`_putwch` \) 到输出字符。  每个 `argument`（如果有）根据 `format` 中相应的格式规范转换和输出。  该格式具有和 [printf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) 中的 `format` 参数相同的窗体和功能。  不同于 `fprintf`、`printf`和 `sprintf` 功能，`_cprintf` 和 `_cwprintf` 输出时不将换行符转换为支持返回换行符 \(CR\-LF\) 组合。  
  
 重要的区别是 `_cwprintf` 在 windows NT 中使用时显示 Unicode 字符。  不同于 `_cprintf`，`_cwprintf` 使用当前控件区域设置。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
 `_cprintf` 验证 `format` 参数.  如果 `format` 是 null 指针，函数会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则该函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcprintf`|`_cprintf`|`_cprintf`|`_cwprintf`|  
|`_tcprintf_l`|`_cprintf_l`|`_cprintf_l`|`_cwprintf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_cprintf`,`_cprintf_l`|\<conio.h\>|  
|`_cwprintf`, `_cwprintf_l`|\<conio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
  **\-16 001d 62511 一个测试**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vfprintf、\_vfprintf\_l、vfwprintf、\_vfwprintf\_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)   
 [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [\_cprintf\_p、\_cprintf\_p\_l、\_cwprintf\_p、\_cwprintf\_p\_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)