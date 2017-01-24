---
title: "分配和取消分配窗口内存 | Microsoft Docs"
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
  - "内存分配, 窗口对象"
  - "内存释放"
  - "内存释放, 窗口内存"
  - "用于窗口对象的存储"
  - "用于窗口对象的存储, 分配"
  - "窗口对象, 释放内存"
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 分配和取消分配窗口内存
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不使用 C\+\+ **删除** 运算符销毁框架窗口或视图。  而是调用 `CWnd` 成员函数 `DestroyWindow`。  框架窗口，因此，与 **new**运算符应的堆分配。  当赋值堆栈上框架的记录时，框架窗口或小心。  堆栈上帧分配其他窗口应尽可能。  
  
## 您想进一步了解什么？  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [窗口的析构序列](../mfc/window-destruction-sequence.md)  
  
-   [将 CWnd 从其 HWND 中分离出来](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## 请参阅  
 [销毁窗口对象](../mfc/destroying-window-objects.md)