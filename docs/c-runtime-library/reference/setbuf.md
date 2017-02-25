---
title: "setbuf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "setbuf"
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
  - "setbuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "setbuf 函数"
  - "流缓冲"
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# setbuf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制流缓冲。  此函数已弃用；使用 [setvbuf](../../c-runtime-library/reference/setvbuf.md)。  
  
## 语法  
  
```  
void setbuf(  
   FILE *stream,  
   char *buffer   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `buffer`  
 用户分配缓冲区。  
  
## 备注  
 `setbuf` 函数控制 `stream`的缓冲。  `stream` 参数必须引用未读取或未编写打开的文件。  如果 `buffer` 参数为 `NULL`，不缓冲的流。  否则，必须指向 `BUFSIZ`缓冲区长度字符数组，`BUFSIZ` 是缓冲区大小。在 STDIO.H. 定义。  用户指定的缓冲区，而不是特定流的默认系统分配的缓冲区，用于缓存使用 I\/O。  `stderr` 是一个非缓冲的流，但默认情况下，可以使用 `setbuf` 将缓冲区为 `stderr`。  
  
 `setbuf` 由 [setvbuf](../../c-runtime-library/reference/setvbuf.md)替换为，是新代码的首选例程。  `setbuf`为现有的代码提供兼容性。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`setbuf`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_setbuf.c  
// compile with: /W3  
// This program first opens files named DATA1 and  
// DATA2. Then it uses setbuf to give DATA1 a user-assigned  
// buffer and to change DATA2 so that it has no buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[BUFSIZ];  
   FILE *stream1, *stream2;  
  
   fopen_s( &stream1, "data1", "a" );  
   fopen_s( &stream2, "data2", "w" );  
  
   if( (stream1 != NULL) && (stream2 != NULL) )  
   {  
      // "stream1" uses user-assigned buffer:  
      setbuf( stream1, buf ); // C4996  
      // Note: setbuf is deprecated; consider using setvbuf instead  
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );  
  
      // "stream2" is unbuffered  
      setbuf( stream2, NULL ); // C4996  
      printf( "stream2 buffering disabled\n" );  
      _fcloseall();  
   }  
}  
```  
  
  **stream1 设置为用户定义的缓冲区。:0012FCDC**  
**stream2 禁用的缓冲**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)