---
title: "文档/视图结构的优点 | Microsoft Docs"
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
  - "文档/视图体系结构, 优点"
  - "视图, 优点"
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 文档/视图结构的优点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要使用 MFC 文档\/视图结构的主要优点是体系结构有很好支持同一文档的多个视图。\(如果不需要多个视图，并且开销小文档\/视图是在额外的应用程序，则您可以避开体系结构。  [Alternatives to the Document\/View Architecture](../mfc/alternatives-to-the-document-view-architecture.md).\)  
  
 假定应用程序允许用户查看数据的数字电子表格形式或为图表形式。  用户可能希望同时查看原始数据，采用电子表格形式该图表数据的结果。  您可以显示各个单独视图在框架窗口或在一个窗口中的拆分器窗格。  现在假设用户可以编辑该电子表格的数据以及查看立即反映的更改在关系图上。  
  
 在 MFC 中，电子表格视图和图表视图基于 CView 派生的不同类。  两个视图将与单文件对象。  文档存储数据 \(可能或获取其从数据库\)。  它们从其检索的两个视图访问文档并显示数据。  
  
 在用户更新某个视图时，该视图对象调用 `CDocument::UpdateAllViews`。  从文档使用，的最新数据函数通知所有文档的视图以及每个视图将相应更新。  为 `UpdateAllViews` 的单个调用同步不同的视图。  
  
 特别是，如果视图存储数据，而数据的分离，视图的此方案难以代码。  文档\/视图，非常容易。  框架为您完成大部分的协调工作。  
  
## 您想进一步了解什么？  
  
-   [选择文档\/视图](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md)  
  
-   [CView::GetDocument](../Topic/CView::GetDocument.md)  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)