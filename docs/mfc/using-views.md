---
title: "使用视图 | Microsoft Docs"
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
  - "CView 类, 视图体系结构"
  - "绘图, 数据"
  - "与视图类的用户和角色交互"
  - "MFC, 视图"
  - "绘制数据"
  - "呈现数据"
  - "用户输入, 通过视图类解释"
  - "视图类, 显示应用程序数据中的角色"
  - "视图类, 管理用户交互中的角色"
  - "视图, using"
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

视图的职责是图形显示文档的数据向用户和接受和解释为操作文档的用户输入。  在使用编写视图类的任务是：  
  
-   编写 [OnDraw](../Topic/CView::OnDraw.md) 视图类的成员函数，呈现文档的数据。  
  
-   连接相应的窗口消息和用户界面对象 \(如菜单项添加到消息处理程序成员函数中视图类。  
  
-   实现这些处理程序解释用户输入。  
  
 此外，还可能需要重写在派生的视图类的其他 `CView` 成员函数。  具体而言，在视图，绘制自己之前，您也可能想重写视图和 [更新时](../Topic/CView::OnUpdate.md)[OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 执行的特殊初始化可以执行任何需要的特殊处理。  对于多文档页，您还必须重写 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 初始化与打印的页以及其他信息数的打印对话框。  有关重写 `CView` 成员函数的更多信息，请参见 [CView](../mfc/reference/cview-class.md) 在 *MFC 参考* 中。  
  
## 您想进一步了解什么？  
  
-   [派生的类可用在 MFC 视图](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [在视图](../mfc/drawing-in-a-view.md)  
  
-   [通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [视图的打印效果。](../mfc/role-of-the-view-in-printing.md)  
  
-   [滚动和缩放视图](../mfc/scrolling-and-scaling-views.md)  
  
-   [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)   
 [CFormView Class](../mfc/reference/cformview-class.md)   
 [记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)