---
title: "拖放： 实现放置源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 301980f7f5a901aa4e2cba40357b18311eef581e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>拖放：实现放置源
此文章介绍了如何获取你的应用程序，以向拖放操作提供数据。  
  
 放置源的基本实现是相对简单。 第一步是确定哪些事件开始拖动操作。 建议用户界面指南定义拖动操作开始为选定的数据和`WM_LBUTTONDOWN`内所选数据点上发生的事件。 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)和[HIERSVR](../visual-cpp-samples.md)请遵循以下准则。  
  
 如果你的应用程序是一个容器，所选的数据链接或嵌入的对象的类型`COleClientItem`，调用其`DoDragDrop`成员函数。 否则，构造`COleDataSource`对象，并用所选内容，将其初始化，调用数据源对象`DoDragDrop`成员函数。 如果你的应用程序服务器，请使用`COleServerItem::DoDragDrop`。 有关自定义标准拖放行为的信息，请参阅文章[拖放： 自定义](../mfc/drag-and-drop-customizing.md)。  
  
 如果`DoDragDrop`返回`DROPEFFECT_MOVE`，立即从源文档中删除源数据。 没有其他返回值从`DoDragDrop`都没有任何效果上放置源。  
  
 有关详细信息，请参见:  
  
-   [实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [自定义拖放](../mfc/drag-and-drop-customizing.md)  
  
-   [创建和销毁 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [操作 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>请参阅  
 [拖放 (OLE)](../mfc/drag-and-drop-ole.md)   
 [Coledatasource:: Dodragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)   
 [COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)   
 [CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)

