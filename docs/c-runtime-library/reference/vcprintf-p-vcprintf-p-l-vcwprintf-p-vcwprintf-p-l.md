---
title: "_vcprintf_p、_vcprintf_p_l、_vcwprintf_p、_vcwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vcprintf_p"
  - "_vcwprintf_p_l"
  - "_vcprintf_p_l"
  - "_vcwprintf_p"
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
  - "vcwprintf_p"
  - "vcprintf_p_l"
  - "_vcprintf_p"
  - "_vcprintf_p_l"
  - "vcwprintf_p_l"
  - "vcprintf_p"
  - "_vcwprintf_p"
  - "_vcwprintf_p_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vcprintf_p 函数"
  - "_vcprintf_p_l 函数"
  - "_vcwprintf_p 函数"
  - "_vcwprintf_p_l 函数"
  - "_vtcprintf_p 函数"
  - "_vtcprintf_p_l 函数"
  - "vcprintf_p 函数"
  - "vcprintf_p_l 函数"
  - "vcwprintf_p 函数"
  - "vcwprintf_p_l 函数"
  - "vtcprintf_p 函数"
  - "vtcprintf_p_l 函数"
ms.assetid: 611024cc-90e7-41db-8e85-145ca95012b1
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _vcprintf_p、_vcprintf_p_l、_vcwprintf_p、_vcwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向参数列表的指针将格式化输出写入到控制台，并支持格式字符串中的位置参数。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _vcprintf_p(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf_p_l(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_p(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_p_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### 参数  
 `format`  
 格式规范。  
  
 `argptr`  
 一个指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 写入的字符数，如果发生输出错误，则为一个负值。  如果 `format` 是 null 指针，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则 `errno` 设置为 `EINVAL` 并返回 \-1。  
  
## 备注  
 这些函数都采用一个指向参数列表的指针，然后使用 `_putch` 函数设置给定数据的格式并将它们写入到控制台。  （`_vcwprintf_p` 使用 `_putwch` 而不是 `_putch`。  `_vcwprintf_p` 是 `_vcprintf_p` 的宽字符版本。  它将采用一个宽字符字符串作为参数。）  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传入的区域设置参数而不是当前线程区域设置。  
  
 每个 `argument`（如果有）根据 `format` 中相应的格式规范进行转换和输出。  格式规范支持位置参数，以便您可以指定参数在格式字符串中的使用顺序。  有关详细信息，请参阅 [printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 当输出换行字符时，这些函数不会将它们转换为回车\-换行符 \(CR\-LF\) 组合。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 这些函数将验证输入指针和格式字符串。  如果 `format` 或 `argument` 为 `NULL`，或者格式字符串包含无效格式字符，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtcprintf_p`|`_vcprintf_p`|`_vcprintf_p`|`_vcwprintf_p`|  
|`_vtcprintf_p_l`|`_vcprintf_p_l`|`_vcprintf_p_l`|`_vcwprintf_p_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_vcprintf_p`, `_vcprintf_p_l`|\<conio.h\> 和 \<stdarg.h\>|  
|`_vcwprintf_p`, `_vcwprintf_p_l`|\<conio.h\> 和 \<stdarg.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vcprintf_p.c  
// compile with: /c  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function that's used to print to the console.  
int eprintf(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf_p(format, args);  
}  
  
int main()  
{  
   int n = eprintf("parameter 2 = %2$d; parameter 1 = %1$s\r\n",  
      "one", 222);  
   _cprintf_s("%d characters printed\r\n");  
}  
```  
  
  **parameter 2 \= 222; parameter 1 \= one**  
**38 characters printed**   
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)