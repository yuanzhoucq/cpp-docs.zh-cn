---
title: "_aligned_recalloc | Microsoft Docs"
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
  - "_aligned_recalloc"
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
  - "aligned_recalloc"
  - "_aligned_recalloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "aligned_recalloc 函数"
  - "_aligned_recalloc 函数"
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改分配 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 存储区的大小和内存初始化为 0。  
  
## 语法  
  
```  
void * _aligned_recalloc(  
   void *memblock,   
   size_t num,  
   size_t size,   
   size_t alignment  
);  
```  
  
#### 参数  
 \[in\] `memblock`  
 当前内存块的指针。  
  
 \[in\] `num`  
 元素的数目。  
  
 \[in\] `size`  
 每个元素的字节大小 。  
  
 \[in\] `alignment`  
 对齐值必须是2的整数次幂。  
  
## 返回值  
 `_aligned_recalloc` 返回一无效指针用来重分配的 \(可能移动）内存块。  如果大小为零，则返回值为 `NULL`，并且缓冲区参数不为 `NULL`，或者如果，没有足够的可用内存块来扩展特定大小的块。  在第一种情况下，释放原始块。  在第二种情况下，原始块是不变。  返回值指向保证适当地存储任何类型的对象的对齐的存储空间。  若要获取指向类型的指针而不是void，请对返回值使用类型转换。  
  
 重新分配内存并更改块的对齐方式是错误的。  
  
## 备注  
 `_aligned_recalloc` 基于 `malloc`。  有关使用 `_aligned_offset_malloc` 的详细信息，请参见[malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果内存分配失败或是如果请求的大小比`_HEAP_MAXREQ` 更大，则函数将 `ENOMEM` 设置为 `errno` 。  有关 `errno`的更多信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_recalloc` 验证其参数。  如果 `alignment` 不是2的幂，此函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这函数返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_recalloc`|\<malloc.h\>|  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)   
 [\_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)