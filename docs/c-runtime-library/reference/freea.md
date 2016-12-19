---
title: "_freea | Microsoft Docs"
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
  - "_freea"
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
  - "freea"
  - "_freea"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_freea 函数"
  - "freea 函数"
  - "内存释放"
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _freea
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

解除分配或释放内存块。  
  
## 语法  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### 参数  
 `memblock`  
 释放之前分配的内存块。  
  
## 返回值  
 无。  
  
## 备注  
 `_freea`  函数解除分配之前通过调用[\_malloca](../../c-runtime-library/reference/malloca.md)、或者 分配的存储区 \(`memblock`\)。  `_freea` 检查内存是否在堆或堆栈分配。  如果在堆栈分配，`_freea` 不执行任何操作。  如果它在堆中分配所释放的字节数与请求的字节数等效，则块分配情况。  如果 `memblock` 为 `NULL`，则忽略指针并且立即返回 `_freea` 。  尝试释放一个无效指针 \(指向未由 `_malloca`，或 分配的存储区的指针\) 可能会影响后续分配请求并导致错误。  
  
 \_`freea` 内部调用 `free`，如果它发现中存在堆分配。  内存是否在堆或堆栈取决于内存中的标记在紧接在分配的内存中的地址。  
  
 如果在释放内存时发生错误，则将 `errno` 设置为操作系统故障的特性信息。  有关详细信息，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 在释放存储区后，[\_heapmin](../../c-runtime-library/reference/heapmin.md) 通过关联未使用的区域和释放它们回操作系统来减少在堆中释放内存的数量。  未释放给操作系统释放的内存被恢复到空闲池并且可再供分配一次。  
  
 对 `_freea` 的调用必须随附的所有调用 `_malloca`。  它也是调用两次 `_freea` 的错误在同一内存。  当应用程序链接 C 运行库的调试版本时，尤其是与 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md) 功能通过定义 `_CRTDBG_MAP_ALLOC`启用，查找缺少或重复的 `_freea`调用。更容易。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `_freea` 是标记的 `__declspec(noalias)`，这意味着函数可确保不修改全局变量。  有关详细信息，请参阅[noalias](../../cpp/noalias.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_freea`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_malloca](../../c-runtime-library/reference/malloca.md)中的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [\_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)