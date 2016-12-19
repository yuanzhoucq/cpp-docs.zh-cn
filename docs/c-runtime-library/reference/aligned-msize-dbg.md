---
title: "_aligned_msize_dbg | Microsoft Docs"
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
  - "_aligned_msize_dbg"
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
  - "_aligned_msize_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_msize_dbg"
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_msize_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回在堆中分配的没存块的大小\(只有调试版本\)。  
  
## 语法  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### 参数  
 \[in\] `memblock`  
 内存块的指针。  
  
 \[in\] `alignment`  
 对齐值必须是2的整数次幂。  
  
 \[in\] `offset`  
 强制对齐内存分配中的偏移量。  
  
## 返回值  
 返回\(以字节为单位\) 作为无符号整数的大小。  
  
## 备注  
 `alignment` 和 `offset`值必须和传递给分配内存块的函数的值一样。  
  
 `_aligned_msize_dbg` 是 [\_aligned\_msize](../../c-runtime-library/reference/aligned-msize.md) 函数的一种调试版本。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，每次减少调用`_aligned_msize_dbg` 而去调用 `_aligned_msize`。  `_aligned_msize` 和 `_aligned_msize_dbg` 计算在基堆中的内存块的大小，但是 `_aligned_msize_dbg` 添加调试功能：它包括在用户部分内存块返回大小的缓存区。  
  
 此函数验证其参数。  如果 `memblock` 是null制造了或 `alignment` 的值不是2，则 `_msize` 会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果错误被处理，函数设置 `errno` 到 `EINVAL` 并返回\-1。  
  
 有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  有关分配块的类型以及它们是如何使用的信息，请参阅 [调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  有关调用一个标准的堆函数及其调试版本在应用程序的调试版本之间的差异，请参阅[堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_msize_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)