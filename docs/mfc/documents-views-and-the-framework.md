---
title: "文档、视图和框架 | Microsoft Docs"
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
  - "应用程序对象 [C++], 与其他 MFC 对象的关系"
  - "应用程序 [MFC]"
  - "文档对象, 与其他 MFC 对象的关系"
  - "文档模板, 模板对象"
  - "文档/视图体系结构, 关于文档/视图体系结构"
  - "文档 [C++]"
  - "MFC [C++], 应用程序框架"
  - "MFC [C++], 文档"
  - "MFC [C++], 视图"
  - "MFC 对象关系"
  - "对象 [C++], MFC 应用程序"
  - "线程对象"
  - "视图对象, 与其他 MFC 对象的关系"
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文档、视图和框架
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

核心 MFC 框架中心是文档和视图的概念。  文档是用户中的编辑会话中进行交互的数据对象。  它通过在 **文件** 菜单的 `New` 或 **打开** 命令文件中创建和通常保存。\(标准 MFC 文档，从类 **CDocument**派生，与活动文档和 OLE 文档不同组合。\)视图是用户与文档窗口交互的对象。  
  
 在运行的应用程序的关键对象是：  
  
-   文档或文档。  
  
     文档类 \(派生自 [CDocument](../mfc/reference/cdocument-class.md)\) 指定应用程序数据。  
  
     如果希望应用程序的 OLE 功能，从其派生类之一派生或 [COleDocument](../mfc/reference/coledocument-class.md) 文档类，根据所需功能的类型。  
  
-   视图或视图。  
  
     视图派生类 \(从 [CView](../mfc/reference/cview-class.md)\) 对数据的用户“窗口”。视图类控件用户如何查找文档的数据并与之交互。  在某些情况下，您可能有文档数据的多个视图。  
  
     如果需要滚动，请从派生。[CScrollView](../mfc/reference/cscrollview-class.md) 如果视图在对话框模板资源。计划的用户界面，请从派生。[CFormView](../mfc/reference/cformview-class.md) 对于简单的文本数据，请使用 [CEditView](../mfc/reference/ceditview-class.md)从或派生。  对于基于窗体的访问，应用程序 \(如数据输入程序，请从 [CRecordView](../mfc/reference/crecordview-class.md) 派生 \(用于 ODBC。\)  可用类、[CTreeView](../mfc/reference/ctreeview-class.md)[CListView](../mfc/reference/clistview-class.md)和 [CRichEditView](../mfc/reference/cricheditview-class.md)。  
  
-   框架窗口  
  
     视图是显示的。“文档框架窗口”。在 SDI 应用程序，文档框架窗口也是“主框架窗口”的应用程序。  在 MDI 应用程序，文档窗口是子窗口显示在主框架窗口内。  派生的主框架窗口类指定样式和视图包含框架窗口的其他特性。  如果需要自定义，请从 [CFrameWnd](../mfc/reference/cframewnd-class.md) 框架窗口派生自定义 SDI 应用程序的文档框架窗口。  从 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 派生自定义 MDI 应用程序的主框架窗口。  并从 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 中派生一个自定义类的应用程序支持的每一个不同 MDI 文档框架窗口。  
  
-   文档模板或模板  
  
     安排、视图和文档模板文件提供框架窗口。  特定文档模板类，从类派生，[CDocTemplate](../mfc/reference/cdoctemplate-class.md)创建和管理一类型的所有打开的文档。  支持的应用程序的多文档的一种类型具有多文档模板。  SDI 为应用程序使用 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) 类或对 MDI 应用程序使用 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) 类。  
  
-   Application 对象  
  
     应用程序类 \(派生自 [CWinApp](../mfc/reference/cwinapp-class.md)\) 控制所有对象上面并指定该应用程序的行为 \(初始化和清理。  应用程序中只具有的应用程序对象创建并管理该应用程序支持的任何文档类型的文档模板。  
  
-   线程对象  
  
     如果您的应用程序创建单独线程执行，例如在后台执行计算 \- 您将使用 [CWinThread](../mfc/reference/cwinthread-class.md)从派生的类。  [CWinApp](../mfc/reference/cwinapp-class.md) 从 `CWinThread` 派生并执行表示 \(或主进程\) 在应用程序主线程。  在辅助线程还可以使用 MFC。  
  
 在正在运行的应用程序，则这些对象而共同响应用户操作边界、由命令和其他消息。  单个应用程序对象管理一个或多个文档模板。  每个文档模板创建并管理一个或多个文档 \(具体取决于应用程序是否是 SDI 或 MDI\)。  用户查看和通过视图来操作文档包含在框架窗口内。  下图演示在这些对象之间的关系。的 SDI 应用程序  
  
 ![正在运行的 SDI 应用程序中的对象](../mfc/media/vc386v1.png "vc386V1")  
运行 SDI 应用程序中的对象  
  
 此系列的其他文章解释框架工具，MFC 应用程序向导"和资源编辑器，如何创建这些对象，它们，而且，您如何编程中使用它们。  文档、视图和框架窗口中 [窗口对象](../mfc/window-objects.md) [文档\/视图结构](../mfc/document-view-architecture.md)和更详细的讨论。  
  
## 请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)