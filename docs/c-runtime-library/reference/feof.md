---
title: "feof | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "feof"
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
  - "feof"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "文件结尾, 测试"
  - "feof 函数"
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# feof
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文件尾的测试在流。  
  
## 语法  
  
```  
int feof(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果读取操作尝试读取超过文件的末尾，则 `feof` 函数将返回非零值；它则返回 0。  如果流指针是`NULL` ，函数会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，`errno` 设置为 `EINVAL`，`feof` 返回0.  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `feof` 例程 \(实现作为函数和宏。\) 确定 `stream` 的结尾是否已通过。  当文件尾时，将读取操作返回文件尾指示符，直到关闭了流或 `rewind`，`fsetpos`、`fseek`或 `clearerr` 调用它。  
  
 例如，在中，如果文件包含 10 字节，并且您阅读 10 字节从文件，`feof` 将返回 0，因为，因此，即使文件指针位于文件的末尾，则未尝试超出结束。阅读。  在尝试读取之后的第 11 个字节将 `feof` 返回一个非零值。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`feof`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_feof.c  
// This program uses feof to indicate when  
// it reaches the end of the file CRT_FEOF.TXT. It also  
// checks for errors with ferror.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int  count, total = 0;  
   char buffer[100];  
   FILE *stream;  
  
   fopen_s( &stream, "crt_feof.txt", "r" );  
   if( stream == NULL )  
      exit( 1 );  
  
   // Cycle until end of file reached:  
   while( !feof( stream ) )  
   {  
      // Attempt to read in 100 bytes:  
      count = fread( buffer, sizeof( char ), 100, stream );  
      if( ferror( stream ) )      {  
         perror( "Read error" );  
         break;  
      }  
  
      // Total up actual bytes read  
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   fclose( stream );  
}  
```  
  
## Input: crt\_feof.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Number of bytes read = 19  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)