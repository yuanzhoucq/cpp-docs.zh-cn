---
title: "_fread_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fread_nolock"
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
  - "_fread_nolock"
  - "fread_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fread_nolock 函数"
  - "数据 [C++], 从输入流中读取"
  - "fread_nolock 函数"
  - "读取数据 [C++], 从输入流"
  - "流 [C++], 读取数据自"
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _fread_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

读取一个数据流，而不锁定其他线程。  
  
## 语法  
  
```  
size_t _fread_nolock(   
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
 指向 `FILE`结构的指针。  
  
## 返回值  
 请参见[fread](../../c-runtime-library/reference/fread.md)。  
  
## 备注  
 此函数是 `fread`的非锁定版本。  它与 `fread` 相同，除了它不受其他线程的干扰保护。  它可能更快，因为它不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fread_nolock`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)