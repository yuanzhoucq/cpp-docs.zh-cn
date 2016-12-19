---
title: "free | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "free"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "free"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "内存块, 解除分配"
  - "free 函数"
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# free
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

解除分配或释放内存块。  
  
## 语法  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### 参数  
 `memblock`  
 释放之前分配的内存块。  
  
## 备注  
 `free` 函数解除分配之前通过调用`calloc`、`malloc`或者 `realloc` 分配的存储区 \(`memblock`\)。  当分配块（或在 `realloc` 情况下重分配）已释放的字节数等于请求的字节数。  如果 `memblock` 为 `NULL`，则忽略指针并且立即返回 `free` 。  尝试释放一个无效指针 \(指向未由 `calloc`，`malloc`或 `realloc` 分配的存储区的指针\) 可能会影响后续分配请求并导致错误。  
  
 如果在释放内存时发生错误，则将 `errno` 设置为操作系统故障的特性信息。  有关详细信息，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 在释放存储区后，[\_heapmin](../../c-runtime-library/reference/heapmin.md) 通过关联未使用的区域和释放它们回操作系统来减少在堆中释放内存的数量。  未释放给操作系统释放的内存被恢复到空闲池并且可再供分配一次。  
  
 当应用程序与调试版本的 C 运行时库连接时，`free` 解析为  [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `free` 是标记的 `__declspec(noalias)`，这意味着函数可确保不修改全局变量。  有关详细信息，请参阅[noalias](../../cpp/noalias.md)。  
  
 使用 [\_malloca](../../c-runtime-library/reference/malloca.md)[\_freea](../../c-runtime-library/reference/freea.md) 释放已分配的内存。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`free`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [malloc](../../c-runtime-library/reference/malloc.md) 示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [\_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_freea](../../c-runtime-library/reference/freea.md)