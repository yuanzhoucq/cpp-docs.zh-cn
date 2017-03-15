---
title: "fread_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fread_s"
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
  - "fread_s"
  - "stdio/fread_s"
dev_langs: 
  - "C++"
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# fread_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取数据。  [](../../c-runtime-library/reference/fread.md "fread")[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 语法  
  
```  
size_t fread_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 参数  
 `buffer`  
 数据的存储位置。  
  
 `bufferSize`  
 需要缓冲区的大小（以字节为单位）。  
  
 `elementSize`  
 写入字节项的大小。  
  
 `count`  
 要读取项目的最大数量。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 `fread_s` 读取到返回缓冲区，`count` 比可能小于 \(全部\) 的项的数目，如果读取错误或文件的结尾，在遇到 `count` 之前。  使用 `feof` 或 `ferror` 函数与一个文件的条件区分错误。  如果 `size` 或 `count` 为 0，则 `fread_s` 返回 0，并且缓冲区内容保持不变。  如果 `stream` or `buffer`是null指针， `fread_s` 则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回0 。  
  
 有关错误代码的更多信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `fread_s` 读取到字节函数 `count` `elementSize` 项从输入 `stream` 且存储在 `buffer`中。与 `stream` 有关的文件指针\(如果有 一个\)由实际读取的字节数增加。  如果特定流在文本模式打开，支架返回换行符对用个换行符替换。  替换没有影响文件指针或返回值的效果。  如果出错，文件指针位置是不确定的。  一个读取项的值不可部分确定。  
  
 此函数锁定其他线程。  如果需要一非锁定版本的，请使用 `_fread_nolock`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fread_s`|\<stdio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```cpp  
  
// crt_fread_s.c  
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c  
//  
// This program opens a file that's named FREAD.OUT and  
// writes characters to the file. It then tries to open  
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
#define BUFFERSIZE 30  
#define DATASIZE 22  
#define ELEMENTCOUNT 2  
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)  
#define FILENAME "FREAD.OUT"  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   for ( i = 0; i < DATASIZE; i++ )  
      list[i] = (char)('z' - i);  
   list[DATASIZE] = '\0'; // terminal null so we can print it  
  
   // Open file in text mode:  
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )  
   {  
      // Write DATASIZE characters to stream   
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );  
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );  
      printf( "Wrote %d items\n\n", numwritten );  
      fclose( stream );  
   } else {  
      printf( "Problem opening the file\n" );  
      return -1;  
   }  
  
   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {  
      // Attempt to read in characters in 2 blocks of 11  
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );  
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );  
      printf( "Contents of buffer after write/read:\n\t%s\n", list );  
      fclose( stream );  
   } else {  
      printf( "File could not be opened\n" );  
      return -1;  
   }  
}  
```  
  
  **读取的缓冲区内容在写入之前\/:**  
 **zyxwvutsrqponmlkjihgfe**  
 **编写多 22 项。**   
 **11 个字节读取的元素数为 2**   
 **读取的缓冲区内容在\/编写后：**   
 **zyxwvutsrqponmlkjihgfe**    
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)