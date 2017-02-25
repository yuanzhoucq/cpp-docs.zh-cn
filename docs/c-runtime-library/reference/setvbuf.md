---
title: "setvbuf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "setvbuf"
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
  - "setvbuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制流缓冲"
  - "setvbuf 函数"
  - "流缓冲"
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# setvbuf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制流缓冲和缓冲区大小。  
  
## 语法  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `buffer`  
 用户分配缓冲区。  
  
 `mode`  
 缓冲模式。  
  
 `size`  
 缓冲区大小\(以字节为单位\)。  允许的范围： 2 \<\= `size` \<\= INT\_MAX \(2147483647\)。  在内部，为 `size` 提供的数值向下舍入到最接近2的倍数。  
  
## 返回值  
 如果成功，则返回0 。  
  
 如果 `stream` 为 `NULL`，或者如果 `mode` 或 `size` 不在有效的变更内，则调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果执行允许继续，这个函数返回 \-1并设定`errno` 到 `EINVAL` 。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `setvbuf` 函数允许程序控制缓冲和 `stream` 的缓冲区大小。  `stream` 必须是指尚未运行 I\/O 操作的打开的文件，因为它已经被打开。  数组指向 `buffer` 用作缓冲区，除非它为 `NULL`，在 `setvbuf` 使用自动分配长度为 `size`\/2 \* 2 个字节的缓冲区的情况下。  
  
 该模式必须为 `_IOFBF`, `_IOLBF` 或 `_IONBF`。  如果 `mode` 为 `_IOFBF` 或 `_IOLBF`，则使用 `size` 作为缓冲区的大小。  如果 `mode` 为 `_IONBF`，则该流不进行缓冲，并且忽略 `size` 和 `buffer` 。  `mode` 的值及其含义为：  
  
 `_IOFBF`  
 完整的缓冲；即 `buffer` 被用作缓冲区并且 `size` 用作缓冲区的大小。  如果 `buffer` 为 `NULL`，会使用一个自动分配缓冲区 `size` 长字节。  
  
 `_IOLBF`  
 对于一些系统，这提供行缓冲。  但是，对于 Win32，行为与 `_IOFBF` 相同 \- 完全缓冲。  
  
 `_IONBF`  
 不管`buffer` 或 `size`，没有使用缓冲区。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`setvbuf`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
  **“stream1” 现在有 1024 字节的缓冲区**  
**“stream2 ”现在没有缓冲区**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)