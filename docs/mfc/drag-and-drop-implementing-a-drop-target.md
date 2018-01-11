---
title: "拖放： 实现放置目标 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9fc73eb6627e63b8013180b7608633a9ee424c92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>拖放：实现放置目标
本文概述了如何使你的应用程序的放置目标。 实现放置目标采用稍多的工作，而不是实现放置源，但是它仍相对简单。 这些技术也适用于非 OLE 应用程序。  
  
#### <a name="to-implement-a-drop-target"></a>若要实现放置目标  
  
1.  将成员变量添加到你想要放置目标应用程序中的每个视图。 此成员变量的类型必须为`COleDropTarget`或从它派生的类。  
  
2.  从处理的视图类的函数`WM_CREATE`消息 (通常`OnCreate`)，调用新成员变量的`Register`成员函数。 `Revoke`将自动为您调用您的视图时销毁。  
  
3.  重写以下函数。 如果希望将相同的行为在整个应用程序，重写视图类中的这些函数。 如果你想要修改在隔离的情况下的行为，或者想要启用删除上非`CView`windows，重写这些函数中的你`COleDropTarget`-派生类。  
  
    |替代|若要允许|  
    |--------------|--------------|  
    |`OnDragEnter`|放在窗口中发生的操作。 当光标首次进入窗口时调用。|  
    |`OnDragLeave`|当在拖动操作离开指定的窗口的特殊行为。|  
    |`OnDragOver`|放在窗口中发生的操作。 当光标拖过窗口时调用。|  
    |`OnDrop`|数据处理的丢弃到指定的窗口。|  
    |`OnScrollBy`|需要滚动时在目标窗口中的特殊行为。|  
  
 请参阅 MAINVIEW。文件中的 MFC OLE 示例的 CPP [OCLIENT](../visual-cpp-samples.md)有关这些函数如何协同工作的示例。  
  
 有关详细信息，请参见:  
  
-   [实现放置源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [创建和销毁 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [操作 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>请参阅  
 [拖放 (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget 类](../mfc/reference/coledroptarget-class.md)
