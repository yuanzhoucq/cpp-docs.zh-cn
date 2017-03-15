---
title: "fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fprintf_s_l"
  - "fwprintf_s"
  - "fprintf_s"
  - "_fwprintf_s_l"
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
  - "_ftprintf_s"
  - "fprintf_s"
  - "fwprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fprintf_s_l 函数"
  - "_ftprintf_s 函数"
  - "_ftprintf_s_l 函数"
  - "_fwprintf_s_l 函数"
  - "fprintf_s 函数"
  - "fprintf_s_l 函数"
  - "ftprintf_s 函数"
  - "ftprintf_s_l 函数"
  - "fwprintf_s 函数"
  - "fwprintf_s_l 函数"
  - "将格式化的数据打印到流"
ms.assetid: 16067c3c-69ce-472a-8272-9aadf1f5beed
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将格式化的数据打印到流  [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
int fprintf_s(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_s_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int fwprintf_s(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_s_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]…  
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `fprintf_s`返回写入的字节数。  `fwprintf_s` 返回编写的宽字符的数目。  在输出错误发生时，这些函数返回负值。  
  
## 备注  
 `fprintf_s`格式化并输出一系列字符和值到输出`stream`*.*每个函数 `argument`（如果有）根据 `format`*.* 中相应的格式规范进行转换和输出。对于 `fprintf_s`，`format` 参数与`printf_s`相同的语法和用法。  
  
 `fwprintf_s` 是 `fprintf_s` 的宽字符版本；`fwprintf_s`，`format`是宽字符串。  如果流在 ANSI 模式中打开，这些函数具有相同的行为。  `fprintf_s` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
 与不安全的版本相似 \(参见 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)\)，如果`stream`和 `format` 是一个 null 指针，这些函数验证其参数并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  这些函数与不安全的版本的不同之处在于格式字符串也需要验证。  如果有任何未知或格式不好的格式化说明符，这些函数调用的参数无效处理程序。  任何情况下，如果允许执行继续，则这些函数返回\-1, 并将`errno`设置为`EINVAL` 。  有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_ftprintf_s`|`fprintf_s`|`fprintf_s`|`fwprintf_s`|  
|`_ftprintf_s_l`|`_fprintf_s_l`|`_fprintf_s_l`|`_fwprintf_s_l`|  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fprintf_s`, `_fprintf_s_l`|\<stdio.h\>|  
|`fwprintf_s`, `_fwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fprintf_s.c  
// This program uses fprintf_s to format various  
// data and print it to the file named FPRINTF_S.OUT. It  
// then displays FPRINTF_S.OUT on the screen using the system  
// function to invoke the operating-system TYPE command.  
  
#include <stdio.h>  
#include <process.h>  
  
FILE *stream;  
  
int main( void )  
{  
   int    i = 10;  
   double fp = 1.5;  
   char   s[] = "this is a string";  
   char   c = '\n';  
  
   fopen_s( &stream, "fprintf_s.out", "w" );  
   fprintf_s( stream, "%s%c", s, c );  
   fprintf_s( stream, "%d\n", i );  
   fprintf_s( stream, "%f\n", fp );  
   fclose( stream );  
   system( "type fprintf_s.out" );  
}  
```  
  
  **这是一个字符串。**  
**10**  
**1.500000**   
## .NET Framework 等效项  
 [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)