---
title: "内存分配 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存分配, 例程"
  - "内存, 分配"
  - "内存, 管理"
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 内存分配
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用这些例程分配、释放和重新分配内存。  
  
### 内存分配例程  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_alloca](../c-runtime-library/reference/alloca.md), [\_malloca](../c-runtime-library/reference/malloca.md)|从堆栈中分配内存|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[calloc](../c-runtime-library/reference/calloc.md)|为数组分配内存，从而将分配的块中的每个字节初始化为 0|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_calloc\_dbg](../c-runtime-library/reference/calloc-dbg.md)|`calloc` 的调试版本；仅在运行时库的调试版本中可用|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[运算符 delete](../c-runtime-library/operator-delete-crt.md)|释放分配的块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[运算符 delete&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|释放分配的块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_expand](../c-runtime-library/reference/expand.md)|展开或收缩内存块，而无需移动它|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_expand\_dbg](../c-runtime-library/reference/expand-dbg.md)|`_expand` 的调试版本；仅在运行时库的调试版本中可用|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[free](../c-runtime-library/reference/free.md)|释放分配的块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_free\_dbg](../c-runtime-library/reference/free-dbg.md)|`free` 的调试版本；仅在运行时库的调试版本中可用|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_freea](../c-runtime-library/reference/freea.md)|从堆栈中释放分配的块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_get\_heap\_handle](../c-runtime-library/reference/get-heap-handle.md)|获取 CRT 堆的 Win32 HANDLE。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapadd](../c-runtime-library/heapadd.md)|将内存添加到堆|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapchk](../c-runtime-library/reference/heapchk.md)|检查堆的一致性|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapmin](../c-runtime-library/reference/heapmin.md)|释放堆中未使用的内存|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapset](../c-runtime-library/heapset.md)|使用指定值填充可用的堆条目|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapwalk](../c-runtime-library/reference/heapwalk.md)|返回有关堆中每个条目的信息|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[malloc](../c-runtime-library/reference/malloc.md)|从堆中分配内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md)|`malloc` 的调试版本；仅在运行时库的调试版本中可用|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_msize](../c-runtime-library/reference/msize.md)|返回分配的块的大小|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_msize\_dbg](../c-runtime-library/reference/msize-dbg.md)|`_msize` 的调试版本；仅在运行时库的调试版本中可用|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[new](../c-runtime-library/operator-new-crt.md)|从堆中分配内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|从堆中分配内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_query\_new\_handler](../c-runtime-library/reference/query-new-handler.md)|返回由 `_set_new_handler` 设置的当前新处理程序例程的地址|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_query\_new\_mode](../c-runtime-library/reference/query-new-mode.md)|返回指示由 `_set_new_mode`  为 `malloc` 设置的新处理程序模式的整数|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[realloc](../c-runtime-library/reference/realloc.md)|将块重新分配到新大小|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_realloc\_dbg](../c-runtime-library/reference/realloc-dbg.md)|`realloc` 的调试版本；仅在运行时库的调试版本中可用|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)|在 `new` 运算符失败（无法分配内存）时启用错误处理机制，然后启用标准模板库 \(STL\) 的编译|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_set\_new\_mode](../c-runtime-library/reference/set-new-mode.md)|设置 `malloc` 的新处理程序模式|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)