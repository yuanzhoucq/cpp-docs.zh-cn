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
ms.openlocfilehash: 74ae94146b1ec711b586ea1fecbbc89a47b40b5e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626270"
---
# <a name="memory-management-resizable-memory-blocks"></a>内存管理：可调整大小的内存块

[内存管理：示例](memory-management-examples.md)一文中介绍的**new**和**delete**运算符非常适合用于分配和分配固定大小的内存块和对象。 有时，应用程序可能需要可调整大小的内存块。 必须使用标准 C 运行时库函数[malloc](../c-runtime-library/reference/malloc.md)、 [realloc](../c-runtime-library/reference/realloc.md)和[free](../c-runtime-library/reference/free.md) ，以管理堆上可调整大小的内存块。

> [!IMPORTANT]
> 将**new**和**delete**运算符与同一内存块上可调整大小的内存分配函数混合在一起会导致 MFC 调试版本中的内存损坏。 不应在使用**new**分配的内存块上使用**realloc** 。 同样，你不应使用**new**运算符分配内存块并将其**删除，或者**对使用**malloc**分配的内存块使用**delete**运算符。

## <a name="see-also"></a>另请参阅
将**new**和**delete**运算符与同一内存块上可调整大小的内存分配函数混合将导致 MFC 的 Debug 版本中的内存损坏。 您不应该在用**new**分配的内存块上使用**realloc**。 同样，您不应该使用**new**运算符分配内存块并使用**free**删除它，或者在使用**malloc**分配的内存块上使用**delete**运算符。


[内存管理：堆分配](memory-management-heap-allocation.md)
