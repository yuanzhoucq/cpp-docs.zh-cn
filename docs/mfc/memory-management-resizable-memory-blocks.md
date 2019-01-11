---
title: 内存管理：可调整大小的内存块
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 499e2d4a99152e08f50159c4c952eb882c9fd425
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481141"
---
# <a name="memory-management-resizable-memory-blocks"></a>内存管理：可调整大小的内存块

[内存管理： 示例](../mfc/memory-management-examples.md)一文中描述的**new**和**delete**运算符适用于分配和释放固定大小的内存块和对象。 有时，您的应用程序可能需要可调整大小的内存块。 您必须使用标准 C 运行时库函数[malloc](../c-runtime-library/reference/malloc.md)， [realloc](../c-runtime-library/reference/realloc.md)和[free](../c-runtime-library/reference/free.md)来管理堆上可调整大小的内存块。

> [!IMPORTANT]
>  混合**new**并**delete**上同一个内存块的可调整大小的内存分配函数的运算符将导致调试版本的 MFC 中损坏的内存。 不应使用**realloc**上的内存块分配**新**。 同样，不应分配的内存块**新**运算符并将其与删除**免费**，或使用**删除**与分配的内存块上的运算符**malloc**。


将**new**和**delete**运算符与同一内存块上可调整大小的内存分配函数混合将导致 MFC 的 Debug 版本中的内存损坏。 您不应该在用**new**分配的内存块上使用**realloc**。 同样，您不应该使用**new**运算符分配内存块并使用**free**删除它，或者在使用**malloc**分配的内存块上使用**delete**运算符。

## <a name="see-also"></a>请参阅

[内存管理：堆分配](../mfc/memory-management-heap-allocation.md)

