---
title: "_flushall | Microsoft Docs"
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
  - "_flushall"
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
  - "_flushall"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "flushall 函数"
  - "刷新流"
  - "流, 刷新"
  - "_flushall 函数"
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _flushall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刷新所有流；清除所有缓冲区。  
  
## 语法  
  
```  
int _flushall( void );  
```  
  
## 返回值  
 `_flushall` 返回打开的流（输入和输出）的数量。  无错误返回。  
  
## 备注  
 默认情况下， `_flushall` 函数写入到相应的文件，该文件所有缓冲区的内容与打开的流相关联。  清除与打开输入流相关联的所有缓冲区的当前内容。\(这些缓冲区通常由操作系统维护，自动确定最佳时间将数据写入磁盘：当缓冲区已满，当关闭了流，或者当程序正常终止，而无需关闭流时。\)  
  
 如果读取跟随对 `_flushall` 调用，则会从输入文件读取新数据到缓冲区中。  在调用 `_flushall` 之后，所有流保持开启。  
  
 运行时库的提交到磁盘的功能，可以确保关键数据直接写入磁盘，而不是操作系统的缓冲区。  无需重写现有的程序，您可以通过链接程序的对象文件与 Commode.obj 启用此功能。  在生成的可执行文件，调用 `_flushall` 将所有缓冲区的内容写入磁盘中。  只有 `_flushall` 和 `fflush` 受 Commode.obj 影响。  
  
 有关控制提交到磁盘的功能的信息，请参阅 [Stream I\/O](../../c-runtime-library/stream-i-o.md)、[fopen](../../c-runtime-library/reference/fopen-wfopen.md) 和 [\_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_flushall`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
  **存在3条刷新过的流。**   
## .NET Framework 等效项  
  
-   [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
-   [System::IO::StreamWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.flush.aspx)  
  
-   [System::IO::TextWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.textwriter.flush.aspx)  
  
-   [System::IO::BinaryWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.flush.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_commit](../../c-runtime-library/reference/commit.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)