---
title: "clearerr_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "clearerr_s"
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
  - "clearerr_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clearerr_s 函数"
  - "针对流的错误指示器"
  - "重置流错误指示器"
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# clearerr_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重置流的错误指示器。  [clearerr](../../c-runtime-library/reference/clearerr.md)[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t clearerr_s(  
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果成功则为0；`EINVAL`如果 `stream`为 NULL。  
  
## 备注  
 `clearerr_s` 函数仅重置错误指示器和文件尾指示符 `stream`。  不会自动清除错误指示符；一次指定流的错误指示器设置，该流中继续，直到操作返回 `clearerr_s``clearerr`，`fseek`，`fsetpos`的错误值，或调用 `rewind`。  
  
 如果 `stream` 为 NULL，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`clearerr_s`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_clearerr_s.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   errno_t err;  
  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      err = clearerr_s( stdin );  
      if (err != 0)  
      {  
         abort();  
      }  
   }  
}  
```  
  
  **`n` 写错误：错误文件说明符**  
**输入是否将导致错误？n**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)