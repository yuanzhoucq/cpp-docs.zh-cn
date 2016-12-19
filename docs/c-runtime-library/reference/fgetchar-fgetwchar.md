---
title: "_fgetchar、_fgetwchar | Microsoft Docs"
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
  - "_fgetchar"
  - "_fgetwchar"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fgetwchar"
  - "_fgettchar"
  - "_fgetchar"
  - "_fgetwchar"
  - "fgettchar"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgetchar 函数"
  - "_fgettchar 函数"
  - "_fgetwchar 函数"
  - "fgetchar 函数"
  - "fgettchar 函数"
  - "fgetwchar 函数"
  - "标准输入, 读取自"
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fgetchar、_fgetwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 `stdin` 中读取字符。  
  
## 语法  
  
```  
int _fgetchar( void );  
wint_t _fgetwchar( void );  
```  
  
## 返回值  
 `_fgetchar` 返回作为 `int` 读取的字符或返回 `EOF` 指示错误或文件结尾。  **\_**`fgetwchar` 返回，作为 [wint\_t](../../c-runtime-library/standard-types.md)，对应于读取字符的宽字符或返回 `WEOF` 指示错误或文件结尾。  对于两个函数，请使用 `feof` 或 `ferror` 区分错误和文件结束的情形。  
  
## 备注  
 这些函数从 `stdin`读取单个字符。  函数增加关联文件指针 \(如果定义\) 指向下一个字符。  如果流是在文件末尾，流的文件结尾指示符已设置。  
  
 `_fgetchar` 与 `fgetc( stdin )` 相等。  与 `getchar`等效，但是作为函数实现，而不是函数和宏。  `_fgetwchar` 是 `_fgetchar`的宽字符版本。  
  
 这些函数与 ANSI 标准不兼容。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fgettchar`|`_fgetchar`|`_fgetchar`|`_fgetwchar`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fgetchar`|\<stdio.h\>|  
|`_fgetwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fgetchar.c  
// This program uses _fgetchar to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[81];  
   int  i, ch;  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = _fgetchar();  
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetchar();  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
}  
```  
  
  **`第一行。 第二行。`第一行。**  
**第二行。**   
## .NET Framework 等效项  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)