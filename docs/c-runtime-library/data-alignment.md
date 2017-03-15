---
title: "数据对齐 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- data.alignment
dev_langs:
- C++
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8c1e9bceaf205f6ac324033842292fe12150df27
ms.lasthandoff: 02/24/2017

---
# <a name="data-alignment"></a>数据对齐
以下 C 运行时函数支持数据对齐。  
  
### <a name="data-alignment-routines"></a>数据对齐例程  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|释放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|释放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块（仅限调试）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|在指定对齐边界分配内存。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|在指定内存边界上为调试标头和覆盖缓冲区分配内存（仅限调试模式）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|返回在堆中分配的存储块的大小。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|返回在堆中分配的内存块的大小（仅限调试版本）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|在指定对齐边界分配内存。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|在指定对齐边界分配内存（仅限调试版本）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小（仅限调试版本）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0（仅限调试版本）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小（仅限调试版本）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0（仅限调试版本）。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
