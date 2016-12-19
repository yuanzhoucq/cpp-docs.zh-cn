---
title: "对象的一阶段和两阶段构建 | Microsoft Docs"
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
  - "对象创建, 图形对象"
  - "对象 [C++], 创建图形对象"
  - "对象 [C++], 图形对象"
  - "对象的一阶段和两阶段构建"
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对象的一阶段和两阶段构建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在两种方法之间的选择。创建图形对象，如钢笔和画笔：  
  
-   *构造一级别*:构造和初始化。一阶段，所有的对象有构造函数。  
  
-   *构造两个阶段*:构造和初始化对象在两个不同的阶段。  构造函数创建对象，这些初始化函数初始化它。  
  
 两阶段结构总是更安全。  在一级别一样，构造函数可能会引发异常，如果您提供了不正确的参数或内存分配失败。  该问题的两阶段结构，避免，尽管您必须检查失败。  在任何情况下，销毁对象是同一过程。  
  
> [!NOTE]
>  这些技术适用于创建所有对象，而不只是对象图。  
  
## 两个构造技术的示例  
 以下简单示例显示构造钢笔对象有两种方法：  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/CPP/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### 您想进一步了解什么？  
  
-   [图形对象](../mfc/graphic-objects.md)  
  
-   [将图形对象选入设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [在视图中绘制](../mfc/drawing-in-a-view.md)  
  
## 请参阅  
 [图形对象](../mfc/graphic-objects.md)