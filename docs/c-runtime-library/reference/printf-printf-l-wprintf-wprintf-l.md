---
title: "printf、_printf_l、wprintf、_wprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_printf_l"
  - "wprintf"
  - "_wprintf_l"
  - "printf"
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
  - "printf"
  - "_tprintf"
  - "wprintf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_printf_l 函数"
  - "_tprintf 函数"
  - "_tprintf_l 函数"
  - "_wprintf_l 函数"
  - "格式化文本 [C++]"
  - "printf 函数"
  - "printf 函数, 格式规范字段"
  - "printf 函数, using"
  - "printf_l 函数"
  - "tprintf 函数"
  - "tprintf_l 函数"
  - "wprintf 函数"
  - "wprintf_l 函数"
  - "写入控制台"
ms.assetid: 77a854ae-5b48-4865-89f4-f2dc5cf80f52
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# printf、_printf_l、wprintf、_wprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将格式化输出打印至标准输出流。  有关这些函数的更多安全版本，请参见 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)。  
  
## 语法  
  
```  
int printf(  
   const char *format [,  
   argument]...   
);  
int _printf_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wprintf(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_l(  
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
 返回打印的字符数，或在发生错误时返回负值。  如果 `format` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则该函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  如果在 `argument` 中遇到 **EOF** \(0xFFFF\)，则函数返回 \-1。  
  
 有关 `errno` 和错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `printf` 函数对一系列字符和值设置格式并将其打印到标准输出流 `stdout` 中。  如果参数紧跟 `format` 字符串，则 `format` 字符串必须包含确定参数输出格式的规范。  `printf` 和 [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) 具有相同的行为，但 `printf` 将输出写入到 `stdout` 而不是 `FILE` 类型的目标。  
  
 `wprintf` 是 `printf` 的宽字符版本；`format` 是宽字符串。  如果流在 ANSI 模式中打开，`wprintf` 和 `printf` 会具有相同的行为。  `printf` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tprintf`|`printf`|`printf`|`wprintf`|  
  
 `format` 参数包括普通字符、转义序列和（如果参数采用 `format`）格式规范。  遵循其外观的序列将普通字符和转义序列复制到 `stdout`。  例如，行：  
  
```  
printf("Line one\n\t\tLine two\n");   
```  
  
 生成输出：  
  
```  
Line one  
        Line two  
```  
  
 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)始终以百分号 \(`%`\) 开头并从左向右读取。  当 `printf` 遇到第一个格式规范（如果有）时，它会转换 `format` 后第一个参数的值并相应地将其输出。  第二种格式规范会导致将第二个参数转换并输出，等等。  如果具有比格式规范更多的参数，则忽略额外的参数。  如果所有的格式规范都没有足够的参数，则结果为未定义。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tprintf`|`printf`|`printf`|`wprintf`|  
|`_tprintf_l`|`_printf_l`|`_printf_l`|`_wprintf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`printf`, `_printf_l`|\<stdio.h\>|  
|`wprintf`, `_wprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_printf.c  
// This program uses the printf and wprintf functions  
// to produce formatted output.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char     ch = 'h',   
            *string = "computer";  
   wchar_t  wch = L'w',   
            *wstring = L"Unicode";  
   int      count = -9234;  
   double   fp = 251.7366;  
  
   // Display integers  
   printf( "Integer formats:\n"  
           "   Decimal: %d  Justified: %.6d  "  
           "Unsigned: %u\n",  
           count, count, count, count );  
  
   // Display decimals  
   printf( "Decimal %d as:\n   Hex: %Xh  "  
           "C hex: 0x%x  Octal: %o\n",  
            count, count, count, count );  
  
   // Display in different radixes  
   printf( "Digits 10 equal:\n   Hex: %i  "  
           "Octal: %i  Decimal: %i\n",  
            0x10, 010, 10 );  
  
   // Display characters  
   printf("Characters in field (1):\n"  
          "%10c%5hc%5C%5lc\n",  
          ch, ch, wch, wch);  
   wprintf(L"Characters in field (2):\n"  
           L"%10C%5hc%5c%5lc\n",  
           ch, ch, wch, wch);  
  
   // Display strings  
   printf("Strings in field (1):\n%25s\n"  
          "%25.4hs\n   %S%25.3ls\n",  
          string, string, wstring, wstring);  
   wprintf(L"Strings in field (2):\n%25S\n"  
           L"%25.4hs\n   %s%25.3ls\n",  
           string, string, wstring, wstring);  
  
   // Display real numbers  
   printf("Real numbers:\n   %f %.2f %e %E\n",  
          fp, fp, fp, fp );  
  
   // Display pointer  
   printf( "\nAddress as:   %p\n", &count);  
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
  
Address as:   0012FF3C  
```  
  
## .NET Framework 等效项  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
-   [System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_fprintf\_p、\_fprintf\_p\_l、\_fwprintf\_p、\_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [\_set\_output\_format](../../c-runtime-library/set-output-format.md)