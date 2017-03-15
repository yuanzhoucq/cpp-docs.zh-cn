---
title: "窗口析构序列 | Microsoft Docs"
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
  - "CWnd 对象, 析构序列"
  - "销毁窗口"
  - "析构, 窗口"
  - "序列 [C++]"
  - "序列 [C++], 窗口析构"
  - "窗口 [C++], 销毁"
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 窗口析构序列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在MFC框架中，当用户关闭帧窗口时，窗口的默认的[OnClose](../Topic/CWnd::OnClose.md) 处理程序调用[DestroyWindow](../Topic/CWnd::DestroyWindow.md)。  最后一次调用的成员函数，当窗口销毁时执行清理，调用 [默认值](../Topic/CWnd::Default.md) [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)窗口是，某些成员函数执行 Windows 清理和最后调用虚成员函数 [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)。  `PostNcDestroy` 的实现 [CFrameWnd](../mfc/reference/cframewnd-class.md) 删除窗口 C\+\+ 对象。  
  
## 您想进一步了解什么？  
  
-   [分配和回收窗口内存](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [将 CWnd 从其 HWND 中分离出来](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## 请参阅  
 [销毁窗口对象](../mfc/destroying-window-objects.md)