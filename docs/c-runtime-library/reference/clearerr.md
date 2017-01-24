---
title: "clearerr | Microsoft Docs"
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
  - "clearerr"
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
  - "clearerr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "clearerr 函数"
  - "针对流的错误指示器"
  - "重置流错误指示器"
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# clearerr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重置流的错误指示器。  提供该函数的一个更安全版本；请参阅 [clearerr\_s](../../c-runtime-library/reference/clearerr-s.md)。  
  
## 语法  
  
```  
void clearerr(  
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 备注  
 `clearerr` 函数仅重置错误指示器和文件尾指示符 `stream`。  不会自动清除错误指示符；一次指定流的错误指示器设置，该流中继续，直到操作返回 `clearerr``fseek`，`fsetpos`，`rewind`的错误值，或调用 。  
  
 如果 `stream` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回。  有关 `errno` 和错误代码的更多信息，请参见 [错误内容](../../c-runtime-library/errno-constants.md)。  
  
 该函数的一个更安全版本可利用；请参阅 [clearerr\_s](../../c-runtime-library/reference/clearerr-s.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`clearerr`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_clearerr.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      clearerr( stdin );  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      clearerr( stdin );  
   }  
   else  
      printf( "No read error\n" );  
}  
```  
  
  **`n` `n` 错误：没有错误**  
**输入是否将导致错误？n**  
**没有显示错误**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)