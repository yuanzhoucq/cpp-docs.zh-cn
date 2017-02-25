---
title: "打印和打印预览 | Microsoft Docs"
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
  - "预览打印"
  - "打印预览"
  - "打印 [C++]"
  - "打印 [C++], 打印预览"
  - "打印 [MFC]"
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 打印和打印预览
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 通过 [CView](../mfc/reference/cview-class.md)类支持打印和打印预览文档的程序。  对于基本打印和打印预览，请重写视图类的 [OnDraw](../Topic/CView::OnDraw.md) 成员函数，则必须执行执行。  该函数可以绘制到屏幕上的视图，以便实际打印机的打印机或设备上下文，到数据对屏幕打印机的设备上下文。  
  
 还可以将代码添加管理页和多文档打印预览，分页打印文档中添加页眉和页脚。它们。  
  
 此系列文章解释如何打印在 Microsoft 基础类库 \(MFC\) 中实现\) 以及如何使用打印结构已内置框架。  文章还说明 MFC 如何支持打印预览功能的简单实现，以及如何使用和修改该功能。  
  
## 您想进一步了解什么？  
  
-   [打印](../mfc/printing.md)  
  
-   [打印预览体系结构](../mfc/print-preview-architecture.md)  
  
-   [示例](../top/visual-cpp-samples.md)  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)