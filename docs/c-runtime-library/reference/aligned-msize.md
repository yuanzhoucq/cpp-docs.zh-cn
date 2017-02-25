---
title: "_aligned_msize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_msize"
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
  - "_aligned_msize"
  - "aligned_msize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_msize 函数"
  - "aligned_msize 函数"
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _aligned_msize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回堆中分配的存储块大小。  
  
## 语法  
  
```  
size_t _msize(  
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
 `_aligned_msize` 函数通过调用[\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_realloc](../../c-runtime-library/reference/aligned-realloc.md)返回分配的内存块的字节大小。  `alignment` 和 `offset`值必须和传递给分配内存块的函数的值一样。  
  
 当应用程序与调试版本的 C 运行时库连接时，`_aligned_msize` 解析为[\_aligned\_msize\_dbg](../../c-runtime-library/reference/aligned-msize-dbg.md)。  有关在调试过程中如何托管堆的详细信息，请参阅  [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 此函数验证其参数。  如果 `memblock` 是null制造了或 `alignment` 的值不是2，则 `_msize` 会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果错误被处理，函数设置 `errno` 到 `EINVAL` 并返回\-1。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_msize`|\<malloc.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)