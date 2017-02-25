---
title: "_putw | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putw"
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
  - "_putw"
  - "putw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_putw 函数"
  - "整数, 写到流"
  - "putw 函数"
  - "流, 将整数写入到"
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _putw
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

向流中写入一个整数。  
  
## 语法  
  
```  
  
      int _putw(  
   int binint,  
   FILE *stream   
);  
```  
  
#### 参数  
 *binint*  
 将二进制整数输出。  
  
 `stream`  
 指向 **FILE** 结构的指针。  
  
## 返回值  
 返回写入的值。  一个`EOF` 的返回值可能会显示一个错误。  因为 `EOF` 也是一个合法的整数值，使用 `ferror` 验证错误。  如果 `stream` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EOF`。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_putw` 函数编写一个二进制值类型 `int` 到 *流的当前位置。* `_putw` 不影响流中项的对齐也不采用任何特殊对齐。  `_putw` 主要是为与以前库兼容。  可移植性问题可能会和 `_putw`同时发生，因为 `int` 的大小和在`int`之内的字节的顺序字节跨系统不同。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_putw`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_putw.c  
/* This program uses _putw to write a  
 * word to a stream, then performs an error check.  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   unsigned u;  
   if( fopen_s( &stream, "data.out", "wb" ) )  
      exit( 1 );  
   for( u = 0; u < 10; u++ )  
   {  
      _putw( u + 0x2132, stream );   /* Write word to stream. */  
      if( ferror( stream ) )         /* Make error check. */  
      {  
         printf( "_putw failed" );  
         clearerr_s( stream );  
         exit( 1 );  
      }  
   }  
   printf( "Wrote ten words\n" );  
   fclose( stream );  
}  
```  
  
## Output  
  
```  
Wrote ten words  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_getw](../../c-runtime-library/reference/getw.md)