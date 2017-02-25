---
title: "创建新文档、窗口和视图 | Microsoft Docs"
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
  - "子窗口, 创建 MDI"
  - "自定义 MFC 默认对象"
  - "文档对象, 创建"
  - "框架窗口 [C++], 创建"
  - "初始化视图"
  - "MDI [C++], 创建窗口"
  - "MDI [C++], 框架窗口"
  - "MFC [C++], 文档"
  - "MFC [C++], 框架窗口"
  - "MFC [C++], 视图"
  - "MFC 默认对象"
  - "MFC 默认对象, 自定义"
  - "对象 [C++], 创建文档对象"
  - "重写, 默认视图行为"
  - "视图对象"
  - "视图对象, 创建"
  - "视图 [C++], 初始化"
  - "视图 [C++], 覆盖默认行为"
  - "窗口对象 [C++], 创建"
  - "窗口 [C++], 创建"
  - "窗口 [C++], MDI"
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建新文档、窗口和视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下图形的文档、视图和框架窗口的创建过程。  关注一对象的其他文章提供更多详细信息。  
  
 在完成了此过程后，团队的对象相互存在而且存储指针。  以下图形显示对象创建的序列。  可以按照从序列图添加到关系图。  
  
 ![用于创建文档的序列](../mfc/media/vc387l1.png "vc387L1")  
文档创建顺序  
  
 ![框架窗口创建序列](../mfc/media/vc387l2.png "vc387L2")  
框架窗口创建顺序  
  
 ![用于创建视图的序列](../mfc/media/vc387l3.png "vc387L3")  
视图创建顺序  
  
 有关如何框架的信息初始化新的文档、视图和框架窗口对象，请参见在 MFC 库引用的类、[CDocument](../mfc/reference/cdocument-class.md)[CView](../mfc/reference/cview-class.md)[CFrameWnd](../mfc/reference/cframewnd-class.md)[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)、、和。  请参见 [技术说明 22](../mfc/tn022-standard-commands-implementation.md)，解释创建和初始化过程进一步的讨论 `New` 和 **打开** 项框架的标准命令的讨论其下在 **文件** 菜单。  
  
##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> 初始化自己添加到这些类  
 前面的图形也建议可以重写成员函数初始化应用程序对象的点。  `OnInitialUpdate` 重写中视图类的初始化是视图的最佳位置。  `OnInitialUpdate` 调用发生，则框架窗口创建之后，然后在框架窗口内的视图与其文档。  例如，在中，如果视图是滚动视图 \(派生自 `CScrollView` 而不是 `CView`\)，应将基于 `OnInitialUpdate` 中重写的文件大小的视图大小。\(此过程在类的说明进行介绍\)。[CScrollView](../mfc/reference/cscrollview-class.md)可以重写 **CDocument** 成员函数 `OnNewDocument` 和 `OnOpenDocument` 提供文档的特定的初始化。  通常，文档，因为可以创建两种方式，必须重写两个。  
  
 在许多情况下，应重写调用的基类版本。  有关更多信息，请参见、[CDocument](../mfc/reference/cdocument-class.md)[CView](../mfc/reference/cview-class.md)[CFrameWnd](../mfc/reference/cframewnd-class.md)[CWinApp](../mfc/reference/cwinapp-class.md) 的名为类、和成员函数在 MFC 库引用。  
  
## 请参阅  
 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档模板创建](../mfc/document-template-creation.md)   
 [文档\/视图创建](../mfc/document-view-creation.md)   
 [MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)