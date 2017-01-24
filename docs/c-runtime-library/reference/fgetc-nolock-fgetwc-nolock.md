---
title: "_fgetc_nolock、_fgetwc_nolock | Microsoft Docs"
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
  - "_fgetc_nolock"
  - "_fgetwc_nolock"
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
  - "_fgetwc_nolock"
  - "fgettc_nolock"
  - "fgetwc_nolock"
  - "_fgetc_nolock"
  - "_fgettc_nolock"
  - "fgetc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgetc_nolock 函数"
  - "_fgettc_nolock 函数"
  - "_fgetwc_nolock 函数"
  - "字符, 读取"
  - "fgetc_nolock 函数"
  - "fgettc_nolock 函数"
  - "fgetwc_nolock 函数"
  - "从流中读取字符"
  - "流, 读取字符自"
ms.assetid: fb8e7c5b-4503-493a-879e-6a1db75aa114
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fgetc_nolock、_fgetwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

读取流中的字符，不锁定线程。  
  
## 语法  
  
```  
int _fgetc_nolock(   
   FILE *stream   
);  
wint_t _fgetwc_nolock(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE`结构的指针。  
  
## 返回值  
 请参见 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)。  
  
## 备注  
 `_fgetc_nolock` 和 `_fgetwc_nolock` 与 `fgetc` 和 `fgetwc`分别是相同的，除了它们不能避免来自由其他线程的干扰。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fgettc_nolock`|`_fgetc_nolock`|`_fgetc_nolock`|`_fgetwc_nolock`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fgetc_nolock`|\<stdio.h\>|  
|`_fgetwc_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fgetc_nolock.c  
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
   if( fopen_s( &stream, "crt_fgetc_nolock.txt", "r" ) != 0 )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetc_nolock( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## 输入:crt\_fgetc\_nolock.txt  
  
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