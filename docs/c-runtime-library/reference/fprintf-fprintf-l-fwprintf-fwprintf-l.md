---
title: "fprintf、_fprintf_l、fwprintf、_fwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwprintf"
  - "fprintf"
  - "_fprintf_l"
  - "_fwprintf_l"
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
  - "fprintf"
  - "fwprintf"
  - "_ftprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fwprintf_l 函数"
  - "fprintf 函数"
  - "fprintf_l 函数"
  - "_fprintf_l 函数"
  - "_ftprintf 函数"
  - "fwprintf 函数"
  - "ftprintf_l 函数"
  - "ftprintf 函数"
  - "_ftprintf_l 函数"
  - "将格式化的数据打印到流"
  - "fwprintf_l 函数"
ms.assetid: 34a87e1c-6e4d-4d48-a611-58314dd4dc4b
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fprintf、_fprintf_l、fwprintf、_fwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将格式化的数据打印到流  提供这些函数的更多安全版本；请参见 [fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)。  
  
## 语法  
  
```  
int fprintf(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int fwprintf(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...  
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
 `fprintf`返回写入的字节数。  `fwprintf` 返回编写的宽字符的数目。  在输出错误发生时，这些函数返回负值。  如果 `stream`或`format`是`NULL`, 则函数调用无效参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)所述.  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  在使用 `fprintf_s` 或 `fwprintf_s`时，格式字符串没有对有效的格式字符进行检查。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `fprintf`格式化并输出一系列字符和值到输出`stream`*.*每个函数 `argument`（如果有）根据 `format`*.* 中相应的格式规范进行转换和输出。对于 `fprintf`，`format` 参数与`printf`相同的语法和用法。  
  
 `fwprintf` 是 `fprintf` 的宽字符版本；`fwprintf`，`format`是宽字符串。  如果流在 ANSI 模式中打开，这些函数具有相同的行为。  `fprintf` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_ftprintf`|`fprintf`|`fprintf`|`fwprintf`|  
|`_ftprintf_l`|`_fprintf_l`|`_fprintf_l`|`_fwprintf_l`|  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fprintf`, `_fprintf_l`|\<stdio.h\>|  
|`fwprintf`, `_fwprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fprintf.c  
/* This program uses fprintf to format various  
 * data and print it to the file named FPRINTF.OUT. It  
 * then displays FPRINTF.OUT on the screen using the system  
 * function to invoke the operating-system TYPE command.  
 */  
  
#include <stdio.h>  
#include <process.h>  
  
FILE *stream;  
  
int main( void )  
{  
   int    i = 10;  
   double fp = 1.5;  
   char   s[] = "this is a string";  
   char   c = '\n';  
  
   fopen_s( &stream, "fprintf.out", "w" );  
   fprintf( stream, "%s%c", s, c );  
   fprintf( stream, "%d\n", i );  
   fprintf( stream, "%f\n", fp );  
   fclose( stream );  
   system( "type fprintf.out" );  
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
 [格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)