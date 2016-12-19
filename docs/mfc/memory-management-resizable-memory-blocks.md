---
title: "内存管理：可调整大小的内存块 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "块, 内存分配"
  - "内存分配, 内存块大小"
  - "内存块, 分配"
  - "内存块, 可调整大小的"
  - "内存, 损坏"
  - "可调整大小的内存块"
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 内存管理：可调整大小的内存块
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**new** 和 **删除** 运算符，介绍文章 [内存管理：示例](../mfc/memory-management-examples.md)，有益于分配和解除分配固定的存储区和对象。  有时，应用程序可能需要的大小可调的存储区。  必须使用标准的 C 运行库函数 [malloc](../c-runtime-library/reference/malloc.md)[realloc](../c-runtime-library/reference/realloc.md)[免](../c-runtime-library/reference/free.md)、和管理在堆的大小可调的存储区。  
  
> [!IMPORTANT]
>  混合 **new** 和 **删除** 运算符与在同一存储区的大小可调的指派功能会在 MFC 调试版本的已损坏内存。  不应对存储区的 `realloc` 分配的 **new**。  同样，不应分配的 **new** 运算符的一个存储区并删除其与 **free**，或者使用 **删除** 运算符使用 `malloc`分配的内存块。  
  
## 请参阅  
 [内存管理：堆分配](../mfc/memory-management-heap-allocation.md)