---
title: "将 CWnd 从其 HWND 中分离出来 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd 对象, 与 HWND 分离"
  - "Detach 方法（CWnd 类）"
  - "将 CWnd 与 HWND 分离"
  - "HWND, 分离 CWnd"
  - "从 CWnd 移除 HWND"
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 将 CWnd 从其 HWND 中分离出来
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果需要避免`HWND` 对象关系，MFC 提供其他 `CWnd` 成员函数，[分离](../Topic/CWnd::Detach.md)，断开窗口窗口的窗口 C\+\+ 对象。  当销毁时，这可以防止窗口销毁窗口对象析构函数。  
  
## 您想进一步了解什么？  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [窗口的析构序列](../mfc/window-destruction-sequence.md)  
  
-   [分配和回收窗口内存](../mfc/allocating-and-deallocating-window-memory.md)  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)