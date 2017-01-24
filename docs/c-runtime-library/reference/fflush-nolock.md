---
title: "_fflush_nolock | Microsoft Docs"
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
  - "_fflush_nolock"
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
  - "fflush_nolock"
  - "_fflush_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fflush_nolock 函数"
  - "fflush_nolock 函数"
  - "刷新"
  - "流, 刷新"
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fflush_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不锁定线程来刷新流。  
  
## 语法  
  
```  
int _fflush_nolock(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE`结构的指针。  
  
## 返回值  
 请参见[fflush](../../c-runtime-library/reference/fflush.md)。  
  
## 备注  
 此函数是 `fflush`的非锁定版本。  它与 `fflush` 相同，除了它不受其他线程的干扰保护。  它可能更快，因为它不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fflush_nolock`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)