---
title: "销毁框架窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PostNcDestroy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Default 方法"
  - "销毁框架窗口"
  - "DestroyWindow 方法"
  - "文档框架窗口, 销毁"
  - "框架窗口 [C++], 销毁"
  - "MFC [C++], 框架窗口"
  - "OnClose 方法"
  - "OnNcDestroy 方法, 和框架窗口"
  - "PostNcDestroy 方法"
  - "窗口 [C++], 销毁"
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 销毁框架窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

管理 MFC 框架窗口销毁以及一些窗口创建与框架的文档和视图。  如果您创建附加窗口，就得销毁它们。  
  
 在框架中，帧，当用户关闭窗口时，窗口的默认调用 [DestroyWindow](../Topic/CWnd::DestroyWindow.md)[OnClose](../Topic/CWnd::OnClose.md) 处理程序。  最后一次调用的成员函数，当窗口销毁时执行清理，调用 [默认值](../Topic/CWnd::Default.md) [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)窗口是，某些成员函数执行 Windows 清理和最后调用虚成员函数 [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)。  `PostNcDestroy` 的实现 [CFrameWnd](../mfc/reference/cframewnd-class.md) 删除窗口 C\+\+ 对象。  不应使用的框架窗口 C\+\+ **删除** 运算符。  请改用 `DestroyWindow`。  
  
 在主窗口关闭时关闭，应用程序将关闭。  如果已经修改的未保存的文档框架，显示消息询问是否应保存文档并确保相应的文档如有必要，保存。  
  
## 您想进一步了解什么？  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)