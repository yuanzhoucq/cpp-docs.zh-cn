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
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364774"
---
# <a name="memory-management-resizable-memory-blocks"></a>内存管理：可调整大小的内存块

新的**new****和删除**运算符，在文章[内存管理：示例](../mfc/memory-management-examples.md)中介绍，非常适合分配和释放固定大小的内存块和对象。 有时，应用程序可能需要可调整大小的内存块。 您必须使用标准的 C 运行时库函数[malloc、realloc](../c-runtime-library/reference/malloc.md)和[免费](../c-runtime-library/reference/free.md)来管理堆上可调整大小的内存块。 [realloc](../c-runtime-library/reference/realloc.md)

> [!IMPORTANT]
> 将**新的**运算符和**删除**运算符与同一内存块上的可调整大小的内存分配函数混合将导致 MFC 的调试版本中的内存损坏。 不应在使用**new**分配的内存块上使用**realloc。** 同样，您不应使用**新**运算符分配内存块，并使用**空闲**的 删除内存块，或使用使用**malloc**分配的内存块上的**删除**运算符。

## <a name="see-also"></a>另请参阅

[内存管理：堆分配](../mfc/memory-management-heap-allocation.md)
