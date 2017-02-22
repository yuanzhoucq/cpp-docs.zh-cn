---
title: "_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cwprintf_s_l"
  - "_cprintf_s_l"
  - "_cprintf_s"
  - "_cwprintf_s"
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
  - "_cwprintf_s_l"
  - "_cprintf_s"
  - "cwprintf_s"
  - "_cprintf_s_l"
  - "cwprintf_s_l"
  - "cprintf_s_l"
  - "_tcprintf_s"
  - "cprintf_s"
  - "_cwprintf_s"
  - "tcprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cprintf_s 函数"
  - "_cprintf_s_l 函数"
  - "_cwprintf_s 函数"
  - "_cwprintf_s_l 函数"
  - "_tcprintf_s 函数"
  - "_tcprintf_s_l 函数"
  - "cprintf_s 函数"
  - "cprintf_s_l 函数"
  - "cwprintf_s 函数"
  - "cwprintf_s_l 函数"
  - "tcprintf_s 函数"
  - "tcprintf_s_l 函数"
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

布局和输出到控件中。  [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _cprintf_s(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_s_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_s(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_s_l(  
   const wchar * format,  
   locale_t locale [,   
   argument] ...  
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
 这些函数设置格式并打印一系列字符和直接显示在控制台的值，使用`_putch`函数输出字符。（`_putwch`适用于`_cwprintf_s` \) 。  每个 `argument`（如果有）根据 `format` 中相应的格式规范转换和输出。  这种格式具有相同的形式和函数作为[printf\_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) 函数的`format` 参数。  不同于 `fprintf_s`、`printf_s`和 `sprintf_s` 功能，`_cprintf_s` 和 `_cwprintf_s` 输出时不将换行符转换为支持返回换行符 \(CR\-LF\) 组合。  
  
 重要的区别是 `_cwprintf_s` 在 windows NT 中使用时显示 Unicode 字符。  不同于 `_cprintf_s`，`_cwprintf_s` 使用当前控制台区域设置。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
 与不安全的版本相似 \(参见 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)\)，如果 `format` 是一个 null 指针，这些函数验证其参数并调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  这些函数与不安全的版本的不同之处在于格式字符串也需要验证。  如果有任何未知或格式不好的格式化说明符，这些函数调用的参数无效处理程序。  任何情况下，如果允许执行继续，则这些函数返回\-1, 并将`errno`设置为`EINVAL` 。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcprintf_s`|`_cprintf_s`|`_cprintf_s`|`_cwprintf_s`|  
|`_tcprintf_s_l`|`_cprintf_s_l`|`_cprintf_s_l`|`_cwprintf_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_cprintf_s`,`_cprintf_s_l`|\<conio.h\>|  
|`_cwprintf_s`, `_cwprintf_s_l`|\<conio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_cprintf_s.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
   int      i = -16, h = 29;  
   unsigned u = 62511;  
   char     c = 'A';  
   char     s[] = "Test";  
  
   /* Note that console output does not translate \n as  
    * standard output does. Use \r\n instead.  
    */  
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
## Output  
  
```  
-16  001d  62511  A Test  
```  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)   
 [vfprintf\_s、\_vfprintf\_s\_l、vfwprintf\_s、\_vfwprintf\_s\_l](../../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)