---
title: "_eof | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_eof"
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
  - "_eof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_eof 函数"
  - "文件结尾"
  - "文件结尾, 测试"
  - "eof 函数"
  - "文件 [C++], 结束"
  - "测试, 用于文件结尾"
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _eof
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文件结尾的测试（EOF）  
  
## 语法  
  
```  
int _eof(   
   int fd   
);  
```  
  
#### 参数  
 `fd`  
 引用开启文件的描述符。  
  
## 返回值  
 `_eof` 返回 1，则当前位置的文件结束，或者 0，如果它不是。  返回值 \- 1 指示错误；在这种情况下，的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，`errno` 设置为 `EBADF`，则指示无效的文件说明符。  
  
## 备注  
 `_eof` 函数确定文件的末尾与 `fd` 是否已到达。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_eof`|\<io.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_eof.c  
// This program reads data from a file  
// ten bytes at a time until the end of the  
// file is reached or an error is encountered.  
//  
#include <io.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh, count, total = 0;  
   char buf[10];  
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
        perror( "Open failed");  
        exit( 1 );  
   }  
   // Cycle until end of file reached:   
   while( !_eof( fh ) )  
   {  
      // Attempt to read in 10 bytes:   
      if( (count = _read( fh, buf, 10 )) == -1 )  
      {  
         perror( "Read error" );  
         break;  
      }  
      // Total actual bytes read   
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   _close( fh );  
}  
```  
  
## Input: crt\_eof.txt  
  
```  
This file contains some text.  
```  
  
### Output  
  
```  
Number of bytes read = 29  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)