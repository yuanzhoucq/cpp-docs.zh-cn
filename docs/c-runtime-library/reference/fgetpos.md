---
title: "fgetpos | Microsoft Docs"
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
  - "fgetpos"
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
  - "fgetpos"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fgetpos 函数"
  - "流, 文件位置指示器"
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgetpos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取流的文件位置的。  
  
## 语法  
  
```  
int fgetpos(   
   FILE *stream,  
   fpos_t *pos   
);  
```  
  
#### 参数  
 `stream`  
 目标流。  
  
 `pos`  
 位置指示器存储。  
  
## 返回值  
 如果成功，`fgetpos`返回 0 。  在失败，则返回非零值并将 `errno` 设置为以下清单常数之一 \(定义在 STDIO.H\):指定 `EBADF`，这意味着的流不是有效指针的文件也不可访问或 `EINVAL`，表示 `stream` 值或 `pos` 值无效，例如，如果其中一为 null 指针。  如果 `stream` 或 `pos` 是一个 `NULL` 指针，函数会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
## 备注  
 `fgetpos` 函数获取 `stream` 参数的位置在当前文件的值并将其存储在 `pos`点为对象。  在调用 `fgetpos` 时，`fsetpos` 函数在 `pos` 以后可以使用重置存储信息 `stream` 参数的指针到它自己的位置。  `pos` 值在格式仅供内部存储和使用。`fgetpos` 和 `fsetpos`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fgetpos`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fgetpos.c  
// This program uses fgetpos and fsetpos to  
// return to a location in a file.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE   *stream;  
   fpos_t pos;  
   char   buffer[20];  
  
   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {  
      perror( "Trouble opening file" );  
      return -1;  
   }  
  
   // Read some data and then save the position.   
   fread( buffer, sizeof( char ), 8, stream );  
   if( fgetpos( stream, &pos ) != 0 ) {  
      perror( "fgetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fgetpos: %.13s\n", buffer );  
  
   // Restore to old position and read data   
   if( fsetpos( stream, &pos ) != 0 ) {  
      perror( "fsetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fsetpos: %.13s\n", buffer );  
   fclose( stream );  
}  
```  
  
## Input: crt\_fgetpos.txt  
  
```  
fgetpos gets a stream's file-position indicator.  
```  
  
### Output crt\_fgetpos.txt  
  
```  
after fgetpos: gets a stream  
after fsetpos: gets a stream  
```  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fsetpos](../../c-runtime-library/reference/fsetpos.md)