---
title: "文档视图体系结构的优点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aad0ed0df5eb25ccc0dd896a5a032cd190b6c3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="advantages-of-the-documentview-architecture"></a>文档/视图结构的优点
使用 MFC 文档/视图体系结构的主要优点是体系结构能够很好地支持同一文档的多个视图。 （如果你不需要多个视图，文档/视图的少量开销为在你的应用程序过多，可以避免体系结构。 [文档/视图结构的替换选项](../mfc/alternatives-to-the-document-view-architecture.md)。)  
  
 假设你的应用程序让用户可以查看的数字数据以电子表格形式或以图表形式呈现。 用户可能想要看到同时这两个原始数据，在电子表格窗体，并从数据产生的图表中。 在单独的框架窗口中或在同一个窗口内的拆分器窗格中显示这些单独的视图。 现在假设用户可以编辑的电子表格和，请参阅中的数据所做的更改立即反映在图表中。  
  
 在 MFC 中，将在不同的类派生自 CView 基于电子表格视图和图表视图。 这两个视图将与单个文档对象相关联。 文档存储数据 （或可能是从数据库中获取它）。 这两个视图访问文档，并显示它们从它检索的数据。  
  
 当用户更新的视图，查看对象的调用之一`CDocument::UpdateAllViews`。 该函数会通知所有文档的视图，并自行使用从文档的最新数据更新每个视图。 对单个调用`UpdateAllViews`同步在不同的视图。  
  
 这种情况下很难对没有分离数据的代码从视图中，尤其是当视图存储的数据本身。 文档/视图后，可以很容易。 框架执行的大部分协调工作为你的操作。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [可选方案可供文档/视图](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)  
  
-   [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)  
  
## <a name="see-also"></a>请参阅  
 [文档/视图体系结构](../mfc/document-view-architecture.md)

