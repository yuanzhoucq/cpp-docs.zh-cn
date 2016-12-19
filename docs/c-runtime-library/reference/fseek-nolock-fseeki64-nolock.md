---
title: "_fseek_nolock、_fseeki64_nolock | Microsoft Docs"
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
  - "_fseek_nolock"
  - "_fseeki64_nolock"
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
apitype: "DLLExport"
f1_keywords: 
  - "_fseek_nolock"
  - "_fseeki64_nolock"
  - "fseek_nolock"
  - "fseeki64_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fseek_nolock 函数"
  - "_fseeki64_nolock 函数"
  - "文件指针 [C++], 移动"
  - "fseek_nolock 函数"
  - "fseeki64_nolock 函数"
  - "查找文件指针"
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fseek_nolock、_fseeki64_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将文件指针移到指定位置。  
  
## 语法  
  
```  
int _fseek_nolock(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64_nolock(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE`结构的指针。  
  
 `offset`  
 `origin.`的字节数  
  
 `origin`  
 初始位置。  
  
## 返回值  
 和 [fseek、\_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md) 相同。  
  
## 备注  
 这些函数分别为 `fseek` 和 `_fseeki64`的非锁定版本。          `fseek` 和 `_fseeki64` 是相同的，除了它们不能避免来自由其他线程的干扰。  这些函数可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fseek`|\<stdio.h\>|  
|`_fseeki64`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
  
-   [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
-   [System::IO::FileStream:::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)