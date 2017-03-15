---
title: "如何：在代码中实现跟踪 | Microsoft Docs"
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
  - "CRectTracker 类, 实现跟踪器"
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：在代码中实现跟踪
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要跟踪一个 OLE 项，必须处理某些事件与项，例如单击该项或更新文档的视图。  在任何情况下，声明一临时和 [种 CRectTracker](../mfc/reference/crecttracker-class.md) 对象通过该对象操作项满足的。  
  
 当用户选中一个项粘贴或与菜单命令对象时，必须初始化 TRACKER 与适当的样式表示 OLE 项的状态。  下表概述 OCLIENT 示例使用的约定。  有关这些控件的更多信息，请参见 `CRectTracker`。  
  
### 将 OLE 项的样式和状态  
  
|显示的样式|OLE 项的状态|  
|-----------|--------------|  
|虚线边框|项链接|  
|固定的边界|项在嵌入到文档|  
|调整大小图柄|该项当前被选定|  
|阴影框|该项当前处于就地活动状态|  
|阴影框项覆盖模式|项的服务器打开|  
  
 您可以处理此初始化轻松使用检查 OLE 项状态并设置适当的样式的过程。  在 OCLIENT 示例中的 **SetupTracker** 函数演示 TRACKER 初始化。  此函数的参数是 *pTracker*地址；对关联到 TRACKER 的客户，`pItem`项的指针；对矩形，*pTrueRect*指针。  有关此函数的更完整的示例，请参见 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md)。  
  
 **SetupTracker** 代码示例提供一种唯一的功能；函数的行已使用交错讨论函数功能的讨论：  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 TRACKER 通过设置最小大小并清除样式 TRACKER 初始化。  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 下面一行检查项当前是否已选择，并且该项是否在链接或嵌入到文档。  在边界内定位的调整大小控点添加到样式，指示项的当前选择。  如果项链接到文档，使用虚线的边框样式。  固定的边框，则嵌入项，使用。  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 如果项当前打开，以下代码将一阴影覆盖模式的项。  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 然后可以调用此函数，必须每当 TRACKER 显示。  例如，请调用从视图类的 `OnDraw` 函数中对此函数。  这更新 TRACKER 的外观，该视图的。  有关完整示例，请参见 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md)中的 **CMainView::OnDraw** 函数。  
  
 在应用程序中，需要 TRACKER 代码，如调整，将检测的事件或进行命中，将发生。  这些操作通常意味着尝试捕获或移动项。  在这些情况下，您需要决定：捕获大小调整手柄或边框的部分在调整大小控点之间的。  `OnLButtonDown` 消息处理程序。测试鼠标位置的适合放置相对于项。  调用 `CRectTracker::HitTest`。  如果测试内容返回除外，**CRectTracker::hitOutside**项调整大小或移动。  因此，应调用 `Track` 成员函数。  为完整示例。参见 MFC OLE 示例中的 **CMainView::OnLButtonDown** 函数。[OCLIENT](../top/visual-cpp-samples.md)  
  
 `CRectTracker` 类提供用于的不同光标指示移动形状，则调整大小，或拖动操作。  处理此事件，检查项鼠标下是否当前选择。  如果它是，请调用 `CRectTracker::SetCursor`或调用默认处理程序。  下面的示例摘自 [OCLIENT](../top/visual-cpp-samples.md)MFC OLE 示例：  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## 请参阅  
 [跟踪器：在您的 OLE 应用程序内实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)