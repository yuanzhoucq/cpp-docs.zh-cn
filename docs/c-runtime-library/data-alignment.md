---
title: 数据对齐 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- data.alignment
dev_langs:
- C++
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa83c067e8a2f6794adde13ed8f163ac7ee52680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="data-alignment"></a>数据对齐

以下 C 运行时函数支持数据对齐。

## <a name="data-alignment-routines"></a>数据对齐例程

|例程所返回的值|使用|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|释放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块。|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|释放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块（仅限调试）。|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|在指定对齐边界分配内存。|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|在指定内存边界上为调试标头和覆盖缓冲区分配内存（仅限调试模式）。|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|返回在堆中分配的存储块的大小。|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|返回在堆中分配的内存块的大小（仅限调试版本）。|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|在指定对齐边界分配内存。|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|在指定对齐边界分配内存（仅限调试版本）。|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小。|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小（仅限调试版本）。|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0（仅限调试版本）。|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小。|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小（仅限调试版本）。|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0。|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|更改使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的内存块的大小，并将该内存初始化为 0（仅限调试版本）。|

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>