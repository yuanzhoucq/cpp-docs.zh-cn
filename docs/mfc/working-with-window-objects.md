---
title: "使用窗口对象 | Microsoft Docs"
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
  - "子窗口, 处理"
  - "窗口对象, 处理"
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 使用窗口对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用与 Windows 使用需要两个活动：  
  
-   处理 Windows 消息  
  
-   绘制窗口中  
  
 若要在所有窗口的窗口消息，包括自己的子窗口，请参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md) 消息映射到 C\+\+ Windows 类。  然后编写消息处理程序在类的成员函数。  
  
 在框架应用程序的大多数图形视图中发生，[OnDraw](../Topic/CView::OnDraw.md) 成员函数调用，就必须绘制窗口的内容。  如果窗口是子视图中，可能将某些视图绘制到子窗口通过 Windows 具有成员函数的 `OnDraw` 调用。  
  
 在任何情况下，需要绘制的设备上下文。  可以使用笔、股票和画笔在设备上下文包含的其他图形对象同窗口关联。  也可以修改这些对象获取所需的绘制。  当设备上下文设置为您喜欢中，调用类 [CDC](../mfc/reference/cdc-class.md) \(设备上下文类的成员函数\) 绘制线条，则形状和文本；使用颜色；并与坐标系统一起使用。  
  
## 您想进一步了解什么？  
  
-   [和消息映射处理](../mfc/message-handling-and-mapping.md)  
  
-   [在视图](../mfc/drawing-in-a-view.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [图形对象](../mfc/graphic-objects.md)  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)