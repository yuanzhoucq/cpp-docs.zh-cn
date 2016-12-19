---
title: "printf_s、_printf_s_l、wprintf_s、_wprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_printf_s_l"
  - "wprintf_s"
  - "_wprintf_s_l"
  - "printf_s"
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
  - "wprintf_s"
  - "printf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_printf_s_l 函数"
  - "_tprintf_s 函数"
  - "_tprintf_s_l 函数"
  - "_wprintf_s_l 函数"
  - "格式化文本 [C++]"
  - "printf 函数, 格式规范字段"
  - "printf 函数, using"
  - "printf_s 函数"
  - "printf_s_l 函数"
  - "tprintf_s 函数"
  - "tprintf_s_l 函数"
  - "wprintf_s 函数"
  - "wprintf_s_l 函数"
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# printf_s、_printf_s_l、wprintf_s、_wprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将格式化输出打印至标准输出流。  [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
## 语法  
  
```  
int printf_s(  
   const char *format [,  
   argument]...   
);  
int _printf_s_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wprintf_s(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_s_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### 参数  
 `format`  
 格式控件。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回打印的字符数，或在发生错误时返回负值。  
  
## 备注  
 `printf_s` 函数对一系列字符和值设置格式并将其打印到标准输出流 `stdout` 中。  如果参数紧跟 *格式* 字符串，`format` 字符串必须包含确定参数输出格式的规范。  
  
 `printf_s` 和 `printf` 之间的一个主要区别是，`printf_s` 检查格式字符串中的有效格式设置字符，而 `printf` 仅检查格式字符串是否为空指针。  如果任一检查失败，将调用无效参数处理程序（在[参数验证](../../c-runtime-library/parameter-validation.md)所述）。  如果允许执行继续，则该函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 有关 `errno` 和错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `printf_s` 和`fprintf_s`具有相同的行为，除了`printf_s`输出到`stdout`而不输出到`FILE`类型。  有关详细信息，请参阅[fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)。  
  
 `wprintf_s` 是 `printf_s` 的宽字符版本；`format` 是宽字符串。  如果流在 ANSI 模式中打开，`wprintf_s` 和 `printf_s` 会具有相同的行为。  `printf_s` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tprintf_s`|`printf_s`|`printf_s`|`wprintf_s`|  
|`_tprintf_s_l`|`_printf_s_l`|`_printf_s_l`|`_wprintf_s_l`|  
  
 `format` 参数包括普通字符、转义序列和（如果参数采用 `format`）格式规范。  遵循其外观的序列将普通字符和转义序列复制到 `stdout`。  例如，行  
  
```  
printf_s("Line one\n\t\tLine two\n");   
```  
  
 生成输出  
  
```  
Line one  
        Line two  
```  
  
 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)始终以百分号 \(`%`\) 开头并从左向右读取。  当 `printf_s` 遇到第一个格式规范（如果有）时，它会转换 `format` 后第一个参数的值并相应地将其输出。  第二种格式规范会导致将第二个参数转换并输出，等等。  如果具有比格式规范更多的参数，则忽略额外的参数。  如果所有的格式规范都没有足够的参数，则结果为未定义。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`printf_s`, `_printf_s_l`|\<stdio.h\>|  
|`wprintf_s`, `_wprintf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_printf_s.c  
/* This program uses the printf_s and wprintf_s functions  
 * to produce formatted output.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   char   ch = 'h', *string = "computer";  
   int    count = -9234;  
   double fp = 251.7366;  
   wchar_t wch = L'w', *wstring = L"Unicode";  
  
   /* Display integers. */  
   printf_s( "Integer formats:\n"  
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",  
           count, count, count );  
  
   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",  
            count, count, count, count );  
  
   /* Display in different radixes. */  
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",  
            0x10, 010, 10 );  
  
   /* Display characters. */  
  
   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);  
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);  
  
   /* Display strings. */  
  
   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",  
   string, string, wstring, wstring);  
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",  
       string, string, wstring, wstring);  
  
   /* Display real numbers. */  
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );  
  
   /* Display pointer. */  
   printf_s( "\nAddress as:   %p\n", &count);  
  
}  
```  
  
## 示例输出  
  
```  
Integer formats:  
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062  
Decimal -9234 as:  
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756  
Digits 10 equal:  
   Hex: 16  Octal: 8  Decimal: 10  
Characters in field (1):  
         h    h    w    w  
Characters in field (2):  
         h    h    w    w  
Strings in field (1):  
                 computer  
                     comp  
   Unicode                      Uni  
Strings in field (2):  
                 computer  
                     comp  
   Unicode                      Uni  
Real numbers:  
   251.736600 251.74 2.517366e+002 2.517366E+002  
  
Address as:   0012FF78  
  
```  
  
## .NET Framework 等效项  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
-   [System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)