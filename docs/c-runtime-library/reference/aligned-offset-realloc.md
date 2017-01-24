---
title: "_aligned_offset_realloc | Microsoft Docs"
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
  - "_aligned_offset_realloc"
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
  - "aligned_offset_realloc"
  - "_aligned_offset_realloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "aligned_offset_realloc 函数"
  - "_aligned_offset_realloc 函数"
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_realloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改使用 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小 。  
  
## 语法  
  
```  
void * _aligned_offset_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### 参数  
 `memblock`  
 当前内存块的指针。  
  
 `size`  
 内存分配的大小。  
  
 `alignment`  
 对齐值必须是2的整数次幂。  
  
 `offset`  
 强制对齐内存分配中的偏移量。  
  
## 返回值  
 `_aligned_offset_realloc` 返回一无效指针用来重分配的 \(可能移动）内存块。  如果大小为零，则返回值为 `NULL`，并且缓冲区参数不为 `NULL`，或者如果，没有足够的可用内存块来扩展特定大小的块。  在第一种情况下，释放原始块。  在第二种情况下，原始块是不变。  返回值指向保证适当地存储任何类型的对象的对齐的存储空间。  若要获取指向类型的指针而不是void，请对返回值使用类型转换。  
  
 `_aligned_offset_realloc` 标记为 `__declspec(noalias)` 和 `__declspec(restrict)`；这意味着函数保证不修改全局变量，和返回的指针不用做别名。  有关更多信息，请参见 [没有别名](../../cpp/noalias.md) 和 [限制](../../cpp/restrict.md)。  
  
## 备注  
 类似于[\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md)，`_aligned_offset_realloc` 允许结构对齐在结构中的偏移量。  
  
 `_aligned_offset_realloc` 基于 `malloc`。  有关使用 `_aligned_offset_malloc` 的详细信息，请参见[malloc](../../c-runtime-library/reference/malloc.md)。  如果 `memblock` 为 `NULL`，则函数调用内部的 `_aligned_offset_malloc`。  
  
 如果内存分配失败或是如果请求的大小比`_HEAP_MAXREQ` 更大，则函数将 `ENOMEM` 设置为 `errno` 。  有关 `errno`的更多信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_offset_realloc` 验证其参数。  如果 `alignment` 不是2的幂次或是如果 `offset` 大于等于 `size` 和非零，这函数调用无效参数处理程序，就如[参数验证](../../c-runtime-library/parameter-validation.md) 描述的。  如果允许执行继续，则这函数返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_offset_realloc`|\<malloc.h\>|  
  
## 示例  
 有关详细信息，请参阅 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## 请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)