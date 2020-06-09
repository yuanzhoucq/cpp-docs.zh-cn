---
title: 内存管理
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 464a31491f2c3017453bdd5bbdc8b059d348eb3c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626261"
---
# <a name="memory-management"></a>内存管理

此系列文章介绍了如何利用与内存管理相关的 Microsoft 基础类库 (MFC) 的通用服务。 内存分配可分为两大类别：帧分配和堆分配。

这两种分配方法之间的一个主要区别是：使用帧分配，您通常可处理实际内存块；使用堆分配，您总是会获得一个指向内存块的指针。 这两个方案之间的另一个主要区别是：帧对象会被自动删除，而堆对象必须由程序员显式删除。

有关 Windows 程序中的内存管理的非 MFC 信息，请参阅 Windows SDK 中的[内存管理](/windows/win32/memory/memory-management)。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [帧分配](memory-management-frame-allocation.md)

- [堆分配](memory-management-heap-allocation.md)

- [分配数组的内存](memory-management-examples.md)

- [从堆中释放数组的内存](memory-management-examples.md)

- [分配数据结构的内存](memory-management-examples.md)

- [分配对象的内存](memory-management-examples.md)

- [可调整大小的内存块](memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)<br/>
[常规 MFC 主题](general-mfc-topics.md)
