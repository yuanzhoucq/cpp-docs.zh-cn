---
title: 内存管理： 可调整大小的内存块 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bbd97899261f85454824fcab261d330b04e25fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="memory-management-resizable-memory-blocks"></a>内存管理：可调整大小的内存块
**新**和**删除**运算符，文所述[内存管理： 示例](../mfc/memory-management-examples.md)，适用于分配和取消分配固定大小的内存块和对象。 有时，你的应用程序可能需要可调整大小的内存块。 你必须使用标准的 C 运行时库函数[malloc](../c-runtime-library/reference/malloc.md)， [realloc](../c-runtime-library/reference/realloc.md)，和[免费](../c-runtime-library/reference/free.md)来管理在堆上的可调整大小的内存块。  
  
> [!IMPORTANT]
>  混合**新**和**删除**上相同的内存块的可调整大小的内存分配函数的运算符将导致损坏的内存，MFC 的调试版本中。 不应使用`realloc`上的内存块分配与**新**。 同样，未分配的内存块，**新**运算符并将其与删除**免费**，或使用**删除**对与分配的内存块的运算符`malloc`.  
  
## <a name="see-also"></a>请参阅  
 [内存管理：堆分配](../mfc/memory-management-heap-allocation.md)

