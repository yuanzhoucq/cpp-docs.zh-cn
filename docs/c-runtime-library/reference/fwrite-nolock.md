---
title: "_fwrite_nolock | Microsoft Docs"
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
  - "_fwrite_nolock"
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
  - "_fwrite_nolock"
  - "fwrite_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fwrite_nolock 函数"
  - "fwrite_nolock 函数"
  - "流, 将数据写入到"
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fwrite_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数据写入到流，但不阻塞线程。  
  
## 语法  
  
```  
size_t _fwrite_nolock(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 参数  
 `buffer`  
 指向要写入文件的数据的指针。  
  
 `size`  
 项目大小 \(以字节为单位\)。  
  
 `count`  
 要写入项目的最大数量。  
  
 `stream`  
 指向 `FILE`结构的指针。  
  
## 返回值  
 与 [fwrite](../../c-runtime-library/reference/fwrite.md) 相同。  
  
## 备注  
 此函数是 `fwrite`的非锁定版本。  它与 `fwrite` 相同，除了它不受其他线程的干扰保护。  它可能更快，因为它不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fwrite_nolock`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [fread](../../c-runtime-library/reference/fread.md) 示例。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_write](../../c-runtime-library/reference/write.md)