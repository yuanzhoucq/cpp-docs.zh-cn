---
title: "_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vcprintf_s"
  - "_vcprintf_s_l"
  - "_vcwprintf_s"
  - "_vcwprintf_s_l"
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
  - "vcprintf_s"
  - "vcwprintf_s_l"
  - "_vcwprintf_s"
  - "_vcwprintf_s_l"
  - "_vcprintf_s_l"
  - "_vtcprintf_s"
  - "vcwprintf_s"
  - "vcprintf_s_l"
  - "_vcprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vcprintf_s 函数"
  - "_vcprintf_s_l 函数"
  - "_vcwprintf_s 函数"
  - "_vcwprintf_s_l 函数"
  - "_vtcprintf_s 函数"
  - "_vtcprintf_s_l 函数"
  - "格式化文本 [C++]"
  - "vcprintf_s 函数"
  - "vcprintf_s_l 函数"
  - "vcwprintf_s 函数"
  - "vcwprintf_s_l 函数"
  - "vtcprintf_s 函数"
  - "vtcprintf_s_l 函数"
ms.assetid: 5a46d45a-30db-45df-9850-455cbdac5636
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向参数列表的指针编写格式化输出到控制台。  [\_vcprintf、\_vcprintf\_l、\_vcwprintf、\_vcwprintf\_l](../../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _vcprintf(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_s(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_s_l(  
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
  
 有关详细信息，请参阅[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 读取字符数，或在发生错误时返回负值。  
  
 类似于这些安全版本较低的函数，如果 `format` 是 null 指针，无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  此外，与这些安全版本较低的函数不同，如果 `format` 不指定有效格式，无效参数将引发异常。  如果允许继续执行，这些函数返回错误代码并设置 `errno` 为该错误代码。  如果更具体的值不适用，默认值错误代码是 `EINVAL`。  
  
## 备注  
 每个函数通过指针指向参数列表，然后布局和编写特定数据到控制台。  `_vcwprintf_s` 是 `_vcprintf_s`的宽字符版本。  它采用宽字符字符串作为参数。  
  
 这些带有 `_l` 后缀的函数版本相同，只不过它们使用通过的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtcprintf_s`|`_vcprintf_s`|`_vcprintf_s`|`_vcwprintf_s`|  
|`_vtcprintf_s_l`|`_vcprintf_s_l`|`_vcprintf_s_l`|`_vcwprintf_s_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_vcprintf_s`, `_vcprintf_s_l`|\<conio.h\> 和\<stdarg.h\>|\<varargs.h\>\*|  
|`_vcwprintf_s`, `_vcwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vcprintf_s.cpp  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function used to print to the console.  
int eprintf_s(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf_s(format, args);  
}  
  
int main()  
{  
   eprintf_s("  (%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,  
           "<some error text>");  
   eprintf_s("  (Related to symbol '%s' defined on line %d).\n",  
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