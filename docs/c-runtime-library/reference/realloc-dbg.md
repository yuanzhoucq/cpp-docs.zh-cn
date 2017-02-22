---
title: "_realloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_realloc_dbg"
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
  - "_realloc_dbg"
  - "realloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "重新分配内存块"
  - "realloc_dbg 函数"
  - "内存块, 重新分配"
  - "内存, 重新分配"
  - "_realloc_dbg 函数"
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _realloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过对块进行移动和\/或调整大小（仅限调试版本），重新分配在堆中内存的指定块。  
  
## 语法  
  
```  
void *_realloc_dbg(  
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 参数  
 `userData`  
 以前指定内存块的指针。  
  
 `newSize`  
 为重新分配的块请求大小\(以字节为单位\)。  
  
 `blockType`  
 为重新分配的块请求类型：`_CLIENT_BLOCK` or `_NORMAL_BLOCK`。  
  
 `filename`  
 指向请求 `realloc` 操作或为空的源文件的名称的指针。  
  
 `linenumber`  
 在请求 `realloc` 操作或为空的源文件中的行号。  
  
 `filename` 和 `linenumber` 的参数只有在 `_realloc_dbg` 被明确调用或[\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)预处理器被持续定义时才有效。  
  
## 返回值  
 成功完成后，此函数返回指向重新分配内存块的用户部分的指针，调用新的处理程序函数或返回空。  对于返回行为的完整描述，请参阅下面的备注部分。  有关如何使用新的处理函数的详细信息，请参阅 [realloc](../../c-runtime-library/reference/realloc.md) 函数。  
  
## 备注  
 `_realloc_dbg` 是  [realloc](../../c-runtime-library/reference/realloc.md) 函数的一种调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用`_realloc_dbg` 而去调用 `realloc`。   `realloc` 和 `_realloc_dbg` 在基堆中重新分配内存块，但是 `_realloc_dbg` 提供一些调试特征：块中用户部分任意侧的缓冲区测试是否泄漏，块类型参数跟踪特定的分配类型，并且`filename`\/`linenumber` 信息决定分配请求的来源。  
  
 `_realloc_dbg` 重新分配比请求的`newSize` 稍微更多空间的内存块。  `newSize`可能比初始分配的内存块大小更多或者更少。  通过调试堆管理器来连接调试内存块并且提供应用程序调试头信息和重写缓冲区来使用额外的空间。  重新分配可能会导致移动在堆中原来的内存块到不同的位置，以及改变内存块的大小。  如果移动内存块，则原始块的内容将被覆盖。  
  
 如果内存分配失败，或者需要的内存数量（包括之前提到的开销）超过 `_HEAP_MAXREQ`，那么 `_realloc_dbg` 设置 `errno` 为 `ENOMEM`。  有关这和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  有关调用一个标准的堆函数及其调试版本在应用程序的调试版本之间的差异，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_realloc_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 请参阅 [\_msize\_dbg](../../c-runtime-library/reference/msize-dbg.md) 主题中的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)