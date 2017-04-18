---
title: "内存分配 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c8bbb5b6f634b401889c787977fde866ecd41eaa
ms.lasthandoff: 03/30/2017

---
# <a name="memory-allocation"></a>内存分配
使用这些例程分配、释放和重新分配内存。  
  
### <a name="memory-allocation-routines"></a>内存分配例程  
  
|例程|使用|  
|-------------|---------|  
|[_alloca](../c-runtime-library/reference/alloca.md)、[_malloca](../c-runtime-library/reference/malloca.md)|从堆栈中分配内存|  
|[calloc](../c-runtime-library/reference/calloc.md)|为数组分配内存，从而将分配的块中的每个字节初始化为 0|  
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|`calloc` 的调试版本；仅在运行时库的调试版本中可用|  
|[运算符 delete](../c-runtime-library/operator-delete-crt.md)|释放分配的块|  
|[运算符 &#91;&#93;](../c-runtime-library/delete-operator-crt.md)|释放分配的块|  
|[_expand](../c-runtime-library/reference/expand.md)|展开或收缩内存块，而无需移动它|  
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|`_expand` 的调试版本；仅在运行时库的调试版本中可用|  
|[free](../c-runtime-library/reference/free.md)|释放分配的块|  
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|`free` 的调试版本；仅在运行时库的调试版本中可用|  
|[_freea](../c-runtime-library/reference/freea.md)|从堆栈中释放分配的块|  
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|获取 CRT 堆的 Win32 HANDLE。|  
|[_heapadd](../c-runtime-library/heapadd.md)|将内存添加到堆|  
|[_heapchk](../c-runtime-library/reference/heapchk.md)|检查堆的一致性|  
|[_heapmin](../c-runtime-library/reference/heapmin.md)|释放堆中未使用的内存|  
|[_heapset](../c-runtime-library/heapset.md)|使用指定值填充可用的堆条目|  
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|返回有关堆中每个条目的信息|  
|[malloc](../c-runtime-library/reference/malloc.md)|从堆中分配内存块|  
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|`malloc` 的调试版本；仅在运行时库的调试版本中可用|  
|[_msize](../c-runtime-library/reference/msize.md)|返回分配的块的大小|  
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|`_msize` 的调试版本；仅在运行时库的调试版本中可用|  
|[new](../c-runtime-library/operator-new-crt.md)|从堆中分配内存块|  
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|从堆中分配内存块|  
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|返回由 `_set_new_handler` 设置的当前新处理程序例程的地址|  
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|返回指示由 `_set_new_mode` 为 `malloc` 设置的新处理程序模式的整数|  
|[realloc](../c-runtime-library/reference/realloc.md)|将块重新分配到新大小|  
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|`realloc` 的调试版本；仅在运行时库的调试版本中可用|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|在 `new` 运算符失败（无法分配内存）时启用错误处理机制，然后启用 C++ 标准库的编译|  
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|设置 `malloc` 的新处理程序模式|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
