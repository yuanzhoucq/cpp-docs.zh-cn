---
title: "_recalloc_dbg | Microsoft Docs"
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
  - "_recalloc_dbg"
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
  - "recalloc_dbg"
  - "_recalloc_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_recalloc_dbg 函数"
  - "recalloc_dbg 函数"
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _recalloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新分配数组并将其元素初始化为 0（仅限调试版本）。  
  
## 语法  
  
```  
void *_recalloc_dbg(     void *userData,    size_t num,    size_t size,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 参数  
 `userData`  
 指向之前分配的内存块的指针。  
  
 `num`  
 内存块的请求数量。  
  
 `size`  
 每个内存块的请求大小（以字节为单位）。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 有关分配块类型及其使用方式的信息，请参阅[调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 `NULL`。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 `NULL`。  
  
 仅当已显式调用 `_recalloc_dbg` 或已定义 [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 处理器常量时，才可使用 `filename` 和 `linenumber` 参数。  
  
## 返回值  
 成功完成时，此函数将返回指向重新分配的内存块的用户部分的指针、调用新处理程序函数，或者返回 NULL。  有关返回行为的完整说明，请参阅以下“备注”部分。  有关如何使用新处理程序函数的详细信息，请参阅 [\_recalloc](../../c-runtime-library/reference/recalloc.md) 函数。  
  
## 备注  
 `_recalloc_dbg` 是 [\_recalloc](../../c-runtime-library/reference/recalloc.md) 函数的调试版本。  未定义 [\_DEBUG](../../c-runtime-library/debug.md) 时，每个对 `_recalloc_dbg` 的调用都会减少到对 `_recalloc` 的调用。  `_recalloc` 和 `_recalloc_dbg` 都可重新分配基堆中的内存块，但是 `_recalloc_dbg` 还包含几种调试功能：用于测试泄漏的块的用户部分两侧的缓冲区、用于跟踪特定分配类型的块类型参数，以及用于确定分配请求的源的 `filename`\/`linenumber` 信息。  
  
 `_recalloc_dbg` 将使用比请求大小 \(`num` \* `size`\) 稍多的空间重新分配指定的内存块，请求大小可能会大于或小于最初分配的内存块大小。  其他空间将由调试堆管理器用于链接调试内存块，以及提供具有调试标头信息的应用程序和覆盖缓冲区。  重新分配可能会导致将原始内存块移动到堆中的其他位置，也可能会导致内存块的大小发生更改。  使用值 0xCD 填充该块的用户部分，使用值 0xFD 填充每个覆盖缓冲区。  
  
 如果内存分配失败，则 `_recalloc_dbg` 将 `errno` 设置为 `ENOMEM`；如果所需的内存量（包括之前提到过的开销）超过 `_HEAP_MAXREQ`，则返回 `EINVAL`。  有关此错误代码和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关在应用程序的调试版本中调用标准堆函数及其调试版本之间的差异的信息，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_recalloc_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)