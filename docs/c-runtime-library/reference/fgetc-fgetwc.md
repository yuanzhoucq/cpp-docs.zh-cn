---
title: "fgetc、fgetwc | Microsoft Docs"
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
  - "fgetwc"
  - "fgetc"
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
  - "_fgettc"
  - "fgetwc"
  - "fgetc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgettc 函数"
  - "字符, 读取"
  - "fgetc 函数"
  - "fgettc 函数"
  - "fgetwc 函数"
  - "从流中读取字符"
  - "流, 读取字符自"
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgetc、fgetwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取一个字符。  
  
## 语法  
  
```  
int fgetc(   
   FILE *stream   
);  
wint_t fgetwc(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 `fgetc` 返回作为 `int` 读取的字符或返回`EOF` 指示错误或文件结尾。  `_fgetwc`[](../../c-runtime-library/standard-types.md "Standard Types") 返回，作为 `wint_tWEOF，对应于读取字符的宽字符或返回`  指示错误或文件结尾。  对于两个函数，请使用 `feof` 或 `ferror` 区分错误和文件结束的情形。  如果阅读错误，流的错误指示器设置。  如果 `stream`是`NULL`，`fgetc` 和`fgetwc`调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`EOF`。  
  
## 备注  
 这些函数每个读取文件的当前位置的单个字符相关联的 `stream`。  函数增加关联文件指针 \(如果定义\) 指向下一个字符。  如果流是在文件末尾，流的文件结尾指示符已设置。  
  
 `getc`与 `fgetc`等效，但是仅实现为函数，而不是函数和宏。  
  
 `fgetwc` 是 `fgetc`的宽字符版本。作为多字节字符字符串或宽字符字符串，并根据 `c` 是否在文本模式或二进制模式打开，  `stream`分别复制宽字符参数。  
  
 除了它们不由其他线程干扰保护，`_nolock` 后缀的版本相同。  
  
 有关处理多字节和宽字符字符的多格式文本和二进制模式，请参见 [在 Unicode 文本和二进制模式的 I\/O 流](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fgettc`|`fgetc`|`fgetc`|`fgetwc`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fgetc`|\<stdio.h\>|  
|`fgetwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fgetc.c  
// This program uses getc to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   char buffer[81];  
   int  i, ch;  
  
   // Open file to read line from:  
   fopen_s( &stream, "crt_fgetc.txt", "r" );  
   if( stream == NULL )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":   
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = fgetc( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## Input: crt\_fgetc.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Line one.  
Line two.  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)