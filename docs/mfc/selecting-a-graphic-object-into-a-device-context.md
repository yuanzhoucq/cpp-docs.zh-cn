---
title: "将图形对象选入设备上下文 | Microsoft Docs"
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
  - "设备上下文, 图形对象"
  - "设备上下文, 选择图形对象"
  - "GDI 对象 [C++], 设备上下文"
  - "图形对象, 选择到设备上下文中"
  - "生存期, 图形对象"
  - "SelectObject 方法"
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将图形对象选入设备上下文
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题适用于使用图形对象在窗口中设备上下文。  在 [创建图形对象](../mfc/one-stage-and-two-stage-construction-of-objects.md)，必须选择到设备上下文来的默认位置存储对象存在后：  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/CPP/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## 生存期图形对象  
 [SelectObject](../Topic/CDC::SelectObject.md) 返回的“图形对象是临时文件”。也就是说，当下次程序获取空闲时，它将删除 `CWinApp` 类的成员函数。[OnIdle](../Topic/CWinApp::OnIdle.md) 只要您在单个函数使用 `SelectObject` 返回的对象，而无需返回控件的主消息循环，则不会有问题。  
  
### 您想进一步了解什么？  
  
-   [图形对象](../mfc/graphic-objects.md)  
  
-   [图形对象的级别和构造两个阶段](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [在视图](../mfc/drawing-in-a-view.md)  
  
## 请参阅  
 [图形对象](../mfc/graphic-objects.md)