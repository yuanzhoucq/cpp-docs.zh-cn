---
title: "数据对齐 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "data.alignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据对齐 [C++]"
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 数据对齐
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的 C 运行时函数支持数据对齐。  
  
### 数据对齐例程  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_aligned\_free](../c-runtime-library/reference/aligned-free.md)|释放[\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)[\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)分配的内存块。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_free\_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|释放由 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块 \(只调试\)。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)|在指定的对齐边界分配内存。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_malloc\_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|在指定的对齐边界分配内存，调试标题的其他空间并覆盖缓冲区 \(仅调试版本\)。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_msize](../c-runtime-library/reference/aligned-msize.md)|返回堆中分配的存储块大小。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_msize\_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|返回在堆中分配的没存块的大小\(只有调试版本\)。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|在指定的对齐边界分配内存。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_malloc\_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|分配内存到指定的对齐边界 \(仅限调试版本\)。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|更改使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小 。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_realloc\_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|更改使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小 \(仅调试版本\) 。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|更改分配 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 存储区的大小和内存初始化为 0。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_recalloc\_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|更改分配 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 存储区的大小和内存初始化为 0（仅限调试版本）。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_realloc](../c-runtime-library/reference/aligned-realloc.md)|更改使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小 。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_realloc\_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|更改使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小 \(仅调试版本\) 。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|更改分配 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 存储区的大小和内存初始化为 0。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_recalloc\_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|更改分配 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 存储区的大小和内存初始化为 0（仅限调试版本）。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)