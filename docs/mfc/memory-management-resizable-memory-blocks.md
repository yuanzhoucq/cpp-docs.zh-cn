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

[内存管理：示例](../mfc/memory-management-examples.md)一文中所述的 **new** 和**delete** 运算符适用于分配和释放固定大小的内存块和对象。 有时，应用程序可能需要可调整大小的内存块。 必须使用标准 C 运行时库函数 [malloc](../c-runtime-library/reference/malloc.md)，[realloc](../c-runtime-library/reference/realloc.md) 和 [free](../c-runtime-library/reference/free.md) 来管理堆上可调整大小的内存块。

> [!IMPORTANT]
>  如果在同一个内存块上将 **new** 和 **delete** 运算符与用于分配大小可调内存的函数混合使用，会导致调试版本的 MFC 中的内存损坏。 不应在使用 **new** 分配的内存快上使用 **realloc**。 不应使用 **new** 运算符分配内存块然后使用 **free** 将其删除，或在使用 **malloc** 分配的内存块上使用 **delete** 运算符。

## <a name="see-also"></a>请参阅

[内存管理：堆分配](../mfc/memory-management-heap-allocation.md)

