---
title: "scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l | Microsoft Docs"
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
  - "wscanf_s"
  - "_wscanf_s_l"
  - "scanf_s"
  - "_scanf_s_l"
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
  - "wscanf_s"
  - "_tscanf_s_l"
  - "_wscanf_s_l"
  - "scanf_s"
  - "_tscanf_s"
  - "_scanf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "从输入流中读取数据 [c + +]"
  - "缓冲区 [C++], 缓冲区溢出"
  - "_scanf_s_l 函数"
  - "_wscanf_s_l 函数"
  - "tscanf_s_l 函数"
  - "tscanf_s 函数"
  - "scanf_s 函数"
  - "从输入流中读取数据 [c + +]"
  - "wscanf_s 函数"
  - "_tscanf_s_l 函数"
  - "_tscanf_s 函数"
  - "scanf_s_l 函数"
  - "从输入流的格式化的数据 [c + +]"
  - "wscanf_s_l 函数"
  - "缓冲区 [C++], 避免溢出"
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
caps.latest.revision: 33
caps.handback.revision: 33
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

读取标准输入流中的格式化数据。 这些版本的 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 具有安全增强功能，如中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
int scanf_s(  
   const char *format [,  
   argument]...   
);  
int _scanf_s_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wscanf_s(  
   const wchar_t *format [,  
   argument]...   
);  
int _wscanf_s_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### 参数  
 `format`  
 格式控制字符串。  
  
 `argument`  
 可选自变量。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回已成功转换和分配的字段数量；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 出现错误时，或者如果第一次尝试读取字符时遇到文件末尾字符或字符串末尾字符，则返回值为 `EOF`。 如果 `format` 是 `NULL` 调用指针，无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则 `scanf_s` 和 `wscanf_s` 返回 `EOF`，并将 `errno` 设置为 `EINVAL`。  
  
 有关这些和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `scanf_s` 函数从标准输入流 `stdin` 中读取数据，并将数据写入到 `argument` 给定的位置。 每个 `argument` 必须为指向类型的变量的指针，该类型与 `format` 中的类型说明符对应。 如果在重叠的字符串之间发生复制，则此行为不确定。  
  
 `wscanf_s` 是 `scanf_s` 的宽字符版本；`format` 的 `wscanf_s` 参数是宽字符字符串。 如果在 ANSI 模式下打开流，则 `wscanf_s` 和 `scanf_s` 的行为相同。`scanf_s` 当前不支持 UNICODE 流的输入。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 与 `scanf` 和 `wscanf` 不同，`scanf_s` 和 `wscanf_s` 要求为类型 `c`、`C`、`s`、`S` 的所有输入参数或 `[]` 中附加的字符串控件集指定缓冲区大小。 字符形式的缓冲区大小作为额外参数，紧跟在指针后面传递到缓冲区或变量。 例如，如果您正在读取一个字符串，则将传递该字符串的缓冲区大小，如下所示：  
  
 `char s[10];`  
  
 `scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9`  
  
 缓冲区大小包括终止 null 字符。 您可以使用宽度规范字段来确保读入的标记可放入缓冲区中。 如果未使用任何宽度规范字段，并且读取的标记太大以致缓冲区中无法容纳，则不会向该缓冲区写入任何内容。  
  
> [!NOTE]
>  大小参数的类型具有 `unsigned`，而不具有 `size_t`。 静态强制转换用于转换 `size_t` 值赋给 `unsigned` 64 位的生成配置。  
  
 以下示例说明缓冲区大小参数描述的是最大字符数而非最大字节数。 在调用 `wscanf_s` 时，缓冲区类型所指示的字符宽度与格式说明符指示的字符宽度不匹配。  
  
```  
wchar_t ws[10];  
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));  
```  
  
 `S` 格式说明符指明了与函数支持的默认宽度“相反的”字符宽度的用法。 该字符宽度是单字节的，而函数支持双字节字符。 此示例可读入最多 9 个单字节宽度字符的字符串，并将其放入一个双字节宽度字符缓冲区中。 这些字符被视为单字节值；头两个字符存储在 `ws[0]` 中，紧接着的两个字符存储在 `ws[1]` 中，依此类推。  
  
 对于字符，可读取单个字符，如下所示：  
  
 `char c;`  
  
 `scanf_s("%c", &c, 1);`  
  
 在读取非 null 终止的字符串的多个字符时，将整数用作宽度规范和缓冲区大小。  
  
 `char c[4];`  
  
 `scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 有关详细信息，请参阅[scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tscanf_s`|`scanf_s`|`scanf_s`|`wscanf_s`|  
|`_tscanf_s_l`|`_scanf_s_l`|`_scanf_s_l`|`_wscanf_s_l`|  
  
 有关详细信息，请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`scanf_s`, `_scanf_s_l`|\<stdio.h\>|  
|`wscanf_s`, `_wscanf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_scanf_s.c  
// This program uses the scanf_s and wscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int      i,  
            result;  
   float    fp;  
   char     c,  
            s[80];  
   wchar_t  wc,  
            ws[80];  
  
   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,  
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );  
   printf( "The number of fields input is %d\n", result );  
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,  
           wc, s, ws);  
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );  
   wprintf( L"The number of fields input is %d\n", result );  
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,  
            c, wc, s, ws);  
}  
```  
  
 当提供此输入时，该程序将生成以下输出：  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
```Output  
字段输入数为的 6 的内容︰ 71 98.599998 h z 字节字符的输入字段的数目为的 6 的内容︰ 36 92.300003 y n 宽字符  
```  
  
## .NET Framework 等效项  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   另请参阅 `Parse` 方法，如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)