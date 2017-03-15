---
title: "_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fwprintf_p"
  - "_fprintf_p_l"
  - "_fwprintf_p_l"
  - "_fprintf_p"
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
  - "_fprintf_p"
  - "_ftprintf_p"
  - "fwprintf_p"
  - "_fwprintf_p"
  - "fprintf_p"
  - "ftprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fprintf_p 函数"
  - "_fprintf_p_l 函数"
  - "_ftprintf_p 函数"
  - "_ftprintf_p_l 函数"
  - "_fwprintf_p 函数"
  - "_fwprintf_p_l 函数"
  - "fprintf_p 函数"
  - "fprintf_p_l 函数"
  - "ftprintf_p 函数"
  - "ftprintf_p_l 函数"
  - "fwprintf_p 函数"
  - "fwprintf_p_l 函数"
  - "打印 [C++], 指向流的格式化数据"
  - "流, 打印格式化数据至"
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将格式化的数据打印到流。  
  
## 语法  
  
```  
int _fprintf_p(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_p_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int _fwprintf_p(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_p_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...  
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE`结构的指针。  
  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 在输出错误时，`_fprintf_p` 和 `_fwprintf_p` 返回写入的字符数或返回负值。  
  
## 备注  
 `_fprintf_p`格式化并输出一系列字符和值到输出`stream`.  每个函数 `argument`（如果有）根据 `format` 中相应的格式规范进行转换和输出。  对于 `_fprintf_p`，`format` 参数与`_printf_p`相同的语法和用法。  这些函数支持位置参数，这意味着格式字符串使用的参数的顺序可更改。  有关位置参数的更多信息，请参见[printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md) 。  
  
 `_fwprintf_p` 是 `_fprintf_p` 的宽字符版本；`_fwprintf_p`，`format`是宽字符串。  如果流在 ANSI 模式中打开，这些函数具有相同的行为。  `_fprintf_p` 当前不支持输出到 UNICODE 流。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
 这些函数与不安全版本相同 \(参见 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)\)，验证它们的参数并调用的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述，如果`stream` 或 `format` 为 null 指针，或如果有任何一种未知或严格的格式说明符。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ftprintf_p`|`_fprintf_p`|`_fprintf_p`|`_fwprintf_p`|  
|`_ftprintf_p_l`|`_fprintf_p_l`|`_fprintf_p_l`|`_fwprintf_p_l`|  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fprintf_p`, `_fprintf_p_l`|\<stdio.h\>|  
|`_fwprintf_p`, `_fwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fprintf_p.c  
// This program uses _fprintf_p to format various  
// data and print it to the file named FPRINTF_P.OUT. It  
// then displays FPRINTF_P.OUT on the screen using the system  
// function to invoke the operating-system TYPE command.  
//   
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
    FILE    *stream = NULL;  
    int     i = 10;  
    double  fp = 1.5;  
    char    s[] = "this is a string";  
    char    c = '\n';  
  
    // Open the file  
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)  
    {  
        // Format and print data  
        _fprintf_p( stream, "%2$s%1$c", c, s );  
        _fprintf_p( stream, "%d\n", i );  
        _fprintf_p( stream, "%f\n", fp );  
  
        // Close the file  
        fclose( stream );  
    }  
  
    // Verify our data  
    system( "type fprintf_p.out" );  
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
 [printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)   
 [\_cprintf\_p、\_cprintf\_p\_l、\_cwprintf\_p、\_cwprintf\_p\_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)   
 [fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)