---
title: "_aligned_offset_malloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_offset_malloc"
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
  - "_aligned_offset_malloc"
  - "aligned_offset_malloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_offset_malloc 函数"
  - "aligned_offset_malloc 函数"
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _aligned_offset_malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的对齐边界分配内存。  
  
## 语法  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### 参数  
 \[in\] `size`  
 请求的内存分配的大小。  
  
 \[in\] `alignment`  
 对齐值必须是2的整数次幂。  
  
 \[in\] `offset`  
 强制对齐内存分配中的偏移量。  
  
## 返回值  
 如果操作失败，则指针指向分配或是为 `NULL`  的内存块。  
  
## 备注  
 在嵌套元素中需要对齐的情况下，`_aligned_offset_malloc` 是有用的；例如，如果在嵌套类中需要对齐。  
  
 `_aligned_offset_malloc` 基于 `malloc`；有关详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 `_aligned_offset_malloc` 标记为 `__declspec(noalias)` 和 `__declspec(restrict)`；这意味着函数保证不修改全局变量，和返回的指针不用做别名。  有关更多信息，请参见 [没有别名](../../cpp/noalias.md) 和 [限制](../../cpp/restrict.md)。  
  
 如果内存分配失败或是如果请求的大小比`_HEAP_MAXREQ` 更大，则函数将 `ENOMEM` 设置为 `errno` 。  有关 `errno`的更多信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_offset_malloc` 验证其参数。  如果 `alignment` 不是2的幂次或是如果 `offset` 大于等于 `size` 和非零，这函数调用无效参数处理程序，就如[参数验证](../../c-runtime-library/parameter-validation.md) 描述的。  如果允许执行继续，则这函数返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_offset_malloc`|\<malloc.h\>|  
  
## 示例  
 有关详细信息，请参阅 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## 请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)