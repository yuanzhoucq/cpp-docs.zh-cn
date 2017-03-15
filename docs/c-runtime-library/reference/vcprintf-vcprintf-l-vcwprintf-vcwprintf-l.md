---
title: "_vcprintf、_vcprintf_l、_vcwprintf、_vcwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vcwprintf"
  - "_vcprintf_l"
  - "_vcwprintf_l"
  - "_vcprintf"
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
  - "_vcwprintf_l"
  - "_vtcprintf"
  - "vcwprintf"
  - "_vcwprintf"
  - "vcprintf_l"
  - "_vcprintf_l"
  - "_vcprintf"
  - "vcprintf"
  - "vcwprintf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vcprintf 函数"
  - "_vcprintf_l 函数"
  - "_vcwprintf 函数"
  - "_vcwprintf_l 函数"
  - "_vtcprintf 函数"
  - "_vtcprintf_l 函数"
  - "格式化文本 [C++]"
  - "vcprintf 函数"
  - "vcprintf_l 函数"
  - "vcwprintf 函数"
  - "vcwprintf_l 函数"
  - "vtcprintf 函数"
  - "vtcprintf_l 函数"
ms.assetid: 4ef8d237-6200-4b66-8731-8c57e5624bb1
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# _vcprintf、_vcprintf_l、_vcwprintf、_vcwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向参数列表的指针编写格式化输出到控制台。  提供这些函数的更多安全版本；请参见 [\_vcprintf\_s、\_vcprintf\_s\_l、\_vcwprintf\_s、\_vcwprintf\_s\_l](../../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _vcprintf(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf_l(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### 参数  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 读取字符数，或在发生错误时返回负值。  如果 `format` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，将 `EINVAL` 设置为 `errno`，并返回 \-1。  
  
## 备注  
 每个函数通过指针指向参数列表，然后布局和编写特定数据到控制台。  `_vcwprintf` 是 `_vcprintf`的宽字符版本。  它采用宽字符字符串作为参数。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtcprintf`|`_vcprintf`|`_vcprintf`|`_vcwprintf`|  
|`_vtcprintf_l`|`_vcprintf_l`|`_vcprintf_l`|`_vcwprintf_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_vcprintf`, `_vcprintf_l`|\<conio.h\> 和\<stdarg.h\>|\<varargs.h\>\*|  
|`_vcwprintf`, `_vcwprintf_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vcprintf.cpp  
// compile with: /c  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function used to print to the console.  
int eprintf(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf(format, args);  
}  
  
int main()  
{  
   eprintf("  (%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,  
           "<some error text>");  
   eprintf("  (Related to symbol '%s' defined on line %d).\n",  
           "<symbol>", 5 );  
}  
```  
  
  **\(10,23\): 错误 C2111: \<某些错误文本\>**  
 **\(与第五行定义的符号 '\<符号\>' 相关 \)。**   
## .NET Framework 等效项  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)