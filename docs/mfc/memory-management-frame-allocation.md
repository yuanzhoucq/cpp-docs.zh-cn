---
title: "内存管理：帧分配 | Microsoft Docs"
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
  - "检测内存泄漏"
  - "帧分配"
  - "帧变量"
  - "帧变量, 自动删除"
  - "堆分配, 与帧分配"
  - "内存分配, frames"
  - "内存泄漏, 在帧上分配对象"
  - "内存泄漏, 检测"
  - "内存泄漏, 帧分配"
  - "内存, 检测泄漏"
  - "内存, 回收"
  - "内存, 释放"
  - "范围, 帧变量"
  - "堆栈帧"
  - "变量, 帧变量"
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 内存管理：帧分配
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在框架分发因其设置为“堆栈帧”名称，只要函数调用。  堆栈帧是暂时存储参数对函数以及任何变量是定义的本机函数。内存的区域。  因为编译器自动为它们分配的空间，帧变量通常称为“自动”变量。  
  
 有关键帧分配的两个特性。  首先，在中，定义局部变量时，堆栈上帧分配足够的空间保存整个变量，因此，即使是一个大数组或数据结构。  接下来，那么，当结构超出范围时，框架变量自动删除：  
  
 [!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/CPP/memory-management-frame-allocation_1.cpp)]  
  
 对于局部变量，此范围转换功能发生，该函数退出，但框架变量的范围小于函数中是否使用嵌套的大括号。  框架变量的此自动删除的非常重要的。  对于简单的基元类型 \(如 `int` 或 **byte**\)，数组或数据结构，变量继续删除的自动使用的内存。  因为变量超出了范围，不能执行访问。  对于 C\+\+ 对象，但是，的自动删除过程会更复杂。  
  
 当对象定义为帧变量时，它会自动调用构造函数。定义遇到的点。  当对象超出范围，其析构函数会自动调用，在对象的内存回收之前。  此自动的构造和析非常方便，但必须知道自动调用，特别是对析构函数。  
  
 分配对帧对象的主要优点是可以自动删除。  当您分配上帧对象时，您不必担心导致内存泄漏的保留下来的对象。\(有关内存泄漏的详细信息，请参见 [在 MFC 中检测内存泄漏](http://msdn.microsoft.com/zh-cn/29ee8909-96e9-4246-9332-d3a8aa8d4658)\) 文章。帧分配的缺点是帧变量不能从它们的范围之外使用。  在所选帧分配的其他因素在堆分配是大结构，并且对象堆，使用代替为堆栈通常存储最好，因为堆栈空间通常是有限的。  
  
## 请参阅  
 [内存管理](../mfc/memory-management.md)