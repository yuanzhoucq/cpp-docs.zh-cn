---
title: "文档/视图结构的纵览 | Microsoft Docs"
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
  - "文档/视图体系结构"
  - "文档/视图体系结构, 关于文档/视图体系结构"
  - "文档/视图体系结构, 从视图访问数据"
  - "文档, 从视图访问数据"
  - "文档, 多个视图"
  - "文档, 视图"
  - "input, 视图类"
  - "多个视图, 从文档更新"
  - "视图, 访问文档数据自"
  - "视图, 和用户输入"
  - "视图, 更新"
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 文档/视图结构的纵览
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在典型的 MFC 应用程序中，文档和视图是匹配的。  数据存储在文档中，但视图具有对数据的访问特权。  文档从视图的分离分隔了数据的存储和显示的维护。  
  
## 从视图访问文档数据  
 视图访问其文档的数据或使用 [GetDocument](../Topic/CView::GetDocument.md) 函数，它返回指向文档的指针，或者通过使视图类成为文档类的 C\+\+ `friend`。  当准备显示或操作数据时，视图使用其对数据的访问获取数据。  
  
 例如，在视图的 [OnDraw](../Topic/CView::OnDraw.md) 成员函数中，视图使用 **GetDocument** 获取文档的指针。  然后它使用该指针访问文档的 `CString` 数据成员。  视图将该字符串传递到 `TextOut` 函数。  若要查看此示例的代码，请参见 [在视图中绘制](../mfc/drawing-in-a-view.md)。  
  
## 对视图的用户输入  
 视图还可能在自身中解释鼠标单击，是选择或编辑数据。  类似的，它也可能将击键解释为数据输入或编辑。  假设用户在视图中输入一字符串管理文本。  视图获取指到文档的指针并使用该指针传递新数据到文档，将其使用某种数据结构存储。  
  
## 更新同一文档的多个视图。  
 在具有同一文档的多个视图的应用程序中 — 如文本编辑器中的拆分窗口 — 视图首先传递新数据到文档。  然后它调用文档的 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 成员函数，它文档的所有视图更新它们自己来反映新的数据。  此同步视图。  
  
### 您想进一步了解什么？  
  
-   [文档\/视图结构的优点](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [文档\/视图结构的替换选项](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)