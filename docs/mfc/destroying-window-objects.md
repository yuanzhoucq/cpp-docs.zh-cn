---
title: "销毁窗口对象 | Microsoft Docs"
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
  - "框架窗口, 销毁"
  - "窗口对象, 删除"
  - "窗口对象, 销毁"
  - "窗口对象, 移除"
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 销毁窗口对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户使用完窗口时，请注意自己的子窗口对象要销毁C\+\+ 窗口对象。  如果这些对象没有被销毁，应用程序将无法恢复这些内存。  所幸，框架在管理了框架窗口、视图和对话框创建的同时，也会管理其的销毁。  如果您创建附加窗口，就得销毁它们。  
  
## 您想进一步了解什么？  
  
-   [窗口的析构序列](../mfc/window-destruction-sequence.md)  
  
-   [分配和回收窗口内存](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [将 CWnd 从其 HWND 中分离出来](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [常用窗口创建序列](../mfc/general-window-creation-sequence.md)  
  
-   [销毁框架窗口](../mfc/destroying-frame-windows.md)  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)