---
title: "getw | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getw"
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
  - "getw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "getw 函数"
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _getw
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中获取整数。  
  
## 语法  
  
```  
int _getw(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE`结构的指针。  
  
## 返回值  
 `_getw` 返回读取的整数值。  返回指示错误或文件结尾的 `EOF` 值。  但是，因为`EOF` 值也是合法的整数值，使用 `feof` 或 `ferror` 来验证文件结尾或错误状态。  如果 `stream` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`EOF`。  
  
## 备注  
 `_getw` 函数从与 `stream` 关联的文件读取类型 `int`的下个二进制值，并增长关联文件指针 \(如果有\) 指向下个未读取字符。  `_getw` 在流中不提供项的任何特殊对齐。  因为 `int` 类型的大小和在 `int` 类型中的字节顺序在系统中有所不同，迁移的问题会伴随 `_getw`出现。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getw`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getw.c  
// This program uses _getw to read a word  
// from a stream, then performs an error check.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   int i;  
  
   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )  
      printf( "Couldn't open file\n" );  
   else  
   {  
      // Read a word from the stream:  
      i = _getw( stream );  
  
      // If there is an error...  
      if( ferror( stream ) )  
      {  
         printf( "_getw failed\n" );  
         clearerr_s( stream );  
      }  
      else  
         printf( "First data word in file: 0x%.4x\n", i );  
      fclose( stream );  
   }  
}  
```  
  
## 输入:crt\_getw.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
First data word in file: 0x656e694c  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_putw](../../c-runtime-library/reference/putw.md)