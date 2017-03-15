---
title: "fread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fread"
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
  - "fread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据 [C++], 从输入流中读取"
  - "fread 函数"
  - "读取数据 [C++], 从输入流"
  - "流 [C++], 读取数据自"
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# fread
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取数据。  
  
## 语法  
  
```  
size_t fread(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 参数  
 `buffer`  
 数据的存储位置。  
  
 `size`  
 项目大小 \(以字节为单位\)。  
  
 `count`  
 要读取项目的最大数量。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 `fread` 返回实际读取的完整项目数，可能小于`count` ，如果出错，或如果在达到之前遇到文件结束 `count`*。*使用 `feof` 或 `ferror` 函数与一个文件的条件区分一个可读错误。  如果 `size` 或 `count` 为 0，则 `fread` 返回 0，并且缓冲区内容保持不变。  如果 `stream` or `buffer`是null指针， `fread` 则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回0 。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `fread` 读取到字节函数 `count` `size` 项从输入 `stream` 且存储在 `buffer`中*。*与 `stream` 有关的文件指针\(如果有 一个\)由实际读取的字节数增加。  如果特定流在文本模式打开，支架返回换行符对用个换行符替换。  替换没有影响文件指针或返回值的效果。  如果出错，文件指针位置是不确定的。  一个读取项的值不可部分确定。  
  
 此函数锁定其他线程。  如果需要一非锁定版本的，请使用 `_fread_nolock`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fread`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fread.c  
// This program opens a file named FREAD.OUT and  
// writes 25 characters to the file. It then tries to open  
// FREAD.OUT and read in 25 characters. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   // Open file in text mode:  
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )  
   {  
      for ( i = 0; i < 25; i++ )  
         list[i] = (char)('z' - i);  
      // Write 25 characters to stream   
      numwritten = fwrite( list, sizeof( char ), 25, stream );  
      printf( "Wrote %d items\n", numwritten );  
      fclose( stream );  
  
   }  
   else  
      printf( "Problem opening the file\n" );  
  
   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )  
   {  
      // Attempt to read in 25 characters   
      numread = fread( list, sizeof( char ), 25, stream );  
      printf( "Number of items read = %d\n", numread );  
      printf( "Contents of buffer = %.25s\n", list );  
      fclose( stream );  
   }  
   else  
      printf( "File could not be opened\n" );  
}  
```  
  
  **编写多 25 项。**  
**项个数为\=25**  
**缓冲区 \= zyxwvutsrqponmlkjihgfedcb**   
## .NET Framework 等效项  
 [System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)