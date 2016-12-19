---
title: "页眉和页脚 | Microsoft Docs"
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
  - "页脚, 打印"
  - "页眉, 打印"
  - "页脚"
  - "页脚, 打印"
  - "页眉"
  - "页眉, 打印"
  - "打印 [MFC], 页眉和页脚"
  - "打印 [MFC], 多页文档"
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 页眉和页脚
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何添加页眉和页脚添加到打印文档。  
  
 当查看屏幕上文档时，文档的名称中的当前位置。标题栏和状态栏通常显示。  在查看文档的打印副本时，在页眉或页脚和页码显示的名称很有用。  这甚至 WYSIWYG 程序中的一种常见情况下它们不同执行打印和屏幕显示。  
  
 [OnPrint](../Topic/CView::OnPrint.md) 成员函数是打印页眉或页脚中的适当位置，因为它已针对每调用页，并且，因为它仅用于打印，调用不为屏幕显示。  您可以定义一个页眉或页脚函数输出，并将其传入从 `OnPrint`设备打印机的上下文。  可能需要在调用 [OnDraw](../Topic/CView::OnDraw.md) 原点避免调整窗口范围或排列页面正文重叠标头或脚注。  可能还必须修改 `OnDraw`，因为该页相应的数量的文档可能会减少。  
  
 一种方法抵消页眉或页脚采用的区域将使用 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)的 **m\_rectDraw** 成员。  每次页面打印，该成员初始化与页的可用区域。  如果打印页眉或页脚，然后打印该页的主体之前，应当减小在 **m\_rectDraw** 存储矩形的大小以便页眉或页脚采用的区域。  然后 `OnPrint` 可以指 **m\_rectDraw** 查看还有多少区域用于打印页面正文保持。  
  
 不能打印标题或另一个，请从 [OnPrepareDC](../Topic/CView::OnPrepareDC.md)，因为它将调用，在 [CDC](../mfc/reference/cdc-class.md) 的 `StartPage` 成员函数调用之前。  此时，打印机设备上下文将在页边界。  可以仅执行打印从 `OnPrint` 成员函数。  
  
## 您想进一步了解什么？  
  
-   [打印多页文档](../mfc/multipage-documents.md)  
  
-   [分配打印的 GDI 资源](../mfc/allocating-gdi-resources.md)  
  
## 请参阅  
 [打印](../mfc/printing.md)