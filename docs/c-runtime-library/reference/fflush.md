---
title: "fflush | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fflush"
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
  - "fflush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fflush 函数"
  - "刷新"
  - "流, 刷新"
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# fflush
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刷新流。  
  
## 语法  
  
```  
int fflush(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果缓冲区刷新成功，则 `fflush` 返回 0 。  指定流没有缓冲区或只读的打开状态的情况下返回 值 0。  返回值 `EOF` 指示一个错误。  
  
> [!NOTE]
>  如果 `fflush` 返回 `EOF`时，数据可能因为写失败丢失而丢失。  在设置关键错误处理程序，最安全的做法是用 `setvbuf` 函数关闭缓冲区或使用底层 I\/O 例程，例如 `_open`，`_close`和 `_write` 替代 I\/O 流函数。  
  
## 备注  
 `fflush` 函数刷新流。  如果关联 `stream` 的文件输出流，`fflush` 将与流关联的缓冲区内容写到文件中。  如果是输入流，`fflush` 清除缓冲区内容。  `fflush` 否定任何先前的调用效果 `ungetc` 对 `stream`。  此外，`fflush(NULL)` 刷新所有输出流。  流在调用之后保持打开。  `fflush` 不会影响未缓冲的流的效果。  
  
 这些缓冲区通常由操作系统维护，自动确定最佳时间将数据写入磁盘：当缓冲区已满，当关闭了流，或者当程序正常终止，而无需关闭流时。  运行时库的提交到磁盘的功能，可以确保关键数据直接写入磁盘，而不是操作系统的缓冲区。  无需重写现有的程序，您可以通过链接程序的对象文件与 COMMODE.OBJ 启用此功能。  在生成的可执行文件，调用 `_flushall` 将所有缓冲区的内容写入磁盘中。  只有 `_flushall` 和 `fflush` 受 COMMODE.OBJ 影响。  
  
 有关控制提交到磁盘的功能的信息，请参阅 [Stream I\/O](../../c-runtime-library/stream-i-o.md)、[fopen](../../c-runtime-library/reference/fopen-wfopen.md) 和 [\_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
 该函数锁定调用线程并因此是线程安全的。  有关非固定版本，请参见 `_fflush_nolock`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fflush`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fflush.c  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int integer;  
   char string[81];  
  
   // Read each word as a string.  
   printf( "Enter a sentence of four words with scanf: " );  
   for( integer = 0; integer < 4; integer++ )  
   {  
      scanf_s( "%s", string, sizeof(string) );        
      printf( "%s\n", string );  
   }  
  
   // You must flush the input buffer before using gets.   
   // fflush on input stream is an extension to the C standard   
   fflush( stdin );     
   printf( "Enter the same sentence with gets: " );  
   gets_s( string, sizeof(string) );  
   printf( "%s\n", string );  
}  
```  
  
  **`这是一项测试 这是一个测试`  `是测试 这是一个四 testEnter`Enter a sentence of four words with scanf: This is a test**  
**已释放此**   
**为**  
**a**  
**测试**  
**输入同一个句子获取：This is a test**  
**这是一个测试**   
## .NET Framework 等效项  
 [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)