---
title: "内存管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b1350c4f41da4219ae2581f5e93cb95d03a65850
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management"></a>内存管理
此系列文章介绍了如何利用与内存管理相关的 Microsoft 基础类库 (MFC) 的通用服务。 内存分配可分为两大类别：帧分配和堆分配。  
  
 这两种分配方法之间的一个主要区别是：使用帧分配，您通常可处理实际内存块；使用堆分配，您总是会获得一个指向内存块的指针。 这两个方案之间的另一个主要区别是：帧对象会被自动删除，而堆对象必须由程序员显式删除。  
  
 有关 Windows 程序中内存管理的非 MFC 信息，请参阅[内存管理](http://msdn.microsoft.com/library/windows/desktop/aa366779)Windows SDK 中。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [帧分配](../mfc/memory-management-frame-allocation.md)  
  
-   [堆分配](../mfc/memory-management-heap-allocation.md)  
  
-   [为数组分配内存](../mfc/memory-management-examples.md)  
  
-   [从堆中释放数组的内存](../mfc/memory-management-examples.md)  
  
-   [为数据结构分配内存](../mfc/memory-management-examples.md)  
  
-   [对象分配内存](../mfc/memory-management-examples.md)  
  
-   [可调整大小的内存块](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>另请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)

