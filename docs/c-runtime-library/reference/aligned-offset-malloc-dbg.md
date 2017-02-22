---
title: "_aligned_offset_malloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_offset_malloc_dbg"
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
  - "_aligned_offset_malloc_dbg"
  - "aligned_offset_malloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_offset_malloc_dbg 函数"
  - "aligned_offset_malloc_dbg 函数"
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_offset_malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配内存到指定的对齐边界 \(仅限调试版本\)。  
  
## 语法  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 参数  
 \[in\] `size`  
 请求的内存分配的大小。  
  
 \[in\] `alignment`  
 对齐值必须是2的整数次幂。  
  
 \[in\] `offset`  
 强制对齐内存分配中的偏移量。  
  
 \[in\] `filename`  
 指向需要分配操作数或者为空的源文件的名称的指针。  
  
 \[in\] `linenumber`  
 在请求的分配操作数或为空的源文件中的行号。  
  
## 返回值  
 如果操作失败，则指针指向分配或是为 `NULL`  的内存块。  
  
## 备注  
 `_aligned_offset_malloc_dbg` 是 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 函数的一种调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用`_aligned_offset_malloc_dbg` 而去调用 `_aligned_offset_malloc`。   `_aligned_offset_malloc` 和 `_aligned_offset_malloc_dbg` 在基堆中分配内存块，但是 `_aligned_offset_malloc_dbg` 提供一些调试特征：块中用户部分任意侧的缓冲区测试是否泄漏，块类型参数跟踪特定的分配类型，并且`filename`\/`linenumber` 信息决定分配请求的来源。  
  
 `_aligned_offset_malloc_dbg` 分配比请求的`size` 稍微更多空间的内存块。  通过调试堆管理器来连接调试内存块并且提供应用程序调试头信息和重写缓冲区来使用额外的空间。  当分配块时，块的用户部分用 0xCD 值填充，并且每个覆盖缓冲区用 0xFD 值填充。  
  
 在嵌套元素中需要对齐的情况下，`_aligned_offset_malloc_dbg` 是有用的；例如，如果在嵌套类中需要对齐。  
  
 `_aligned_offset_malloc_dbg` 基于 `malloc`；有关详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果内存分配失败或是如果请求的大小比`_HEAP_MAXREQ` 更大，则函数将 `ENOMEM` 设置为 `errno` 。  有关 `errno`的更多信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_offset_malloc` 验证其参数。  如果 `alignment` 不是2的幂次或是如果 `offset` 大于等于 `size` 和非零，这函数调用无效参数处理程序，就如[参数验证](../../c-runtime-library/parameter-validation.md) 描述的。  如果允许执行继续，则这函数返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)