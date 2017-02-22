---
title: "内存管理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存"
  - "内存分配"
  - "内存分配, MFC"
  - "内存, 管理"
  - "MFC, 内存管理"
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 内存管理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文章的此组描述如何使用 Microsoft 基础类库 \(MFC\) 的常规服务与内存管理。  内存分配主要分为两个类别：帧分配和堆分配。  
  
 分配两个方法之间的主要区别是与您通常通过实际存储区的帧分配，而堆分配始终提供指针存储区。  两个方案之间的另一个主要区别是框架自动删除对象，而必须由程序员显式删除堆对象。  
  
 有关内存管理的非 MFC 在窗口中的程序信息，请参阅《[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [内存管理](http://msdn.microsoft.com/library/windows/desktop/aa366779)。  
  
## 您想进一步了解什么？  
  
-   [帧分配](../mfc/memory-management-frame-allocation.md)  
  
-   [堆分配](../mfc/memory-management-heap-allocation.md)  
  
-   [为该数组分配内存](../mfc/memory-management-examples.md)  
  
-   [解除分配数组的内存堆](../mfc/memory-management-examples.md)  
  
-   [结构的内存分配数据](../mfc/memory-management-examples.md)  
  
-   [分配对象的内存。](../mfc/memory-management-examples.md)  
  
-   [可调整大小的内存块](../mfc/memory-management-resizable-memory-blocks.md)  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)