---
title: "何时初始化 CWnd 对象 | Microsoft Docs"
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
  - "CWnd 对象, 在附加 HWND 时"
  - "CWnd 对象, 在初始化时"
  - "HWND, 在附加到 CWnd 对象时"
  - "初始化 CWnd 对象"
  - "初始化对象, CWnd"
  - "窗口对象, 在初始化 CWnd 时"
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 何时初始化 CWnd 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您不能创建自己的子窗口或在 `CWnd` 派生对象的构造函数中调用任何 Windows API 函数。  这是因为，`CWnd` 对象的 `HWND` 尚未创建。  大多数窗口特定的初始化，如添加子窗口，必须在 [OnCreate](../Topic/CWnd::OnCreate.md) 消息处理程序中完成。  
  
## 您想进一步了解什么？  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
-   [文档\/视图创建](../mfc/document-view-creation.md)  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)