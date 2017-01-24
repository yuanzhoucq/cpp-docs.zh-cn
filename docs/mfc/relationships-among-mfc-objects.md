---
title: "MFC 对象之间的关系 | Microsoft Docs"
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
  - "MFC 对象关系"
  - "MFC, 键对象之间的关系"
  - "对象 [C++], 关系"
  - "关系, MFC 对象"
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 对象之间的关系
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要帮助在中心将文档\/视图创建过程，请考虑一运行程序：用于包含框架窗口、文档的视图和视图与文档。  
  
-   文档保留该文档和指针"视图到文档的文档的列表创建模板。  
  
-   视图将指向该文档是它的父框架窗口的子级。  
  
-   文档框架窗口保留一个指向当前活动视图。  
  
-   文档模板将其打开文档的列表。  
  
-   应用程序保留其文档模板的列表。  
  
-   窗口记录所有打开的窗口，以便它可以发送到。  
  
 这些关系在文档\/视图创建时生成。  下表显示在运行的程序的对象如何访问其他对象。  所有对象可以获取指向应用程序通过调用全局函数 [AfxGetApp](../Topic/AfxGetApp.md)。  
  
### 能够对其他应用程序中的对象  
  
|从对象|如何访问其他对象|  
|---------|--------------|  
|Document|使用 [GetFirstViewPosition](../Topic/CDocument::GetFirstViewPosition.md) [GetNextView](../Topic/CDocument::GetNextView.md) 和访问文档的列表视图。<br /><br /> 调用获取文档模板的 [GetDocTemplate](../Topic/CDocument::GetDocTemplate.md)。|  
|视图|调用获取文档中的 [GetDocument](../Topic/CView::GetDocument.md)。<br /><br /> 调用获取框架窗口中 [GetParentFrame](../Topic/CWnd::GetParentFrame.md)。|  
|文档框架窗口|调用获取当前视图的 [GetActiveView](../Topic/CFrameWnd::GetActiveView.md)。<br /><br /> 调用 [GetActiveDocument](../Topic/CFrameWnd::GetActiveDocument.md) 获取文档附加到当前的视图。|  
|MDI帧窗口|调用获取当前有效的 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)的 [MDIGetActive](../Topic/CMDIFrameWnd::MDIGetActive.md)。|  
  
 通常，框架窗口具有视图，但是，在某些情况下，在拆分窗口，则框架窗口包含多个视图。  框架窗口保留一个指向当前活动视图；其他视图，在激活后，指针更新。  
  
> [!NOTE]
>  指针到主框架窗口在应用程序对象的成员变量存储。[m\_pMainWnd](../Topic/CWinThread::m_pMainWnd.md) 对 `OnFileNew` 的调用在 `CWinApp` 的 `InitInstance` 成员函数的重写设置了 `m_pMainWnd`。  如果您不调用 `OnFileNew`，您必须将 `InitInstance` 变量的值。\(SDI\) COM 组件 \(服务器\) 应用程序无法将变量设置，如果 \/Embedding 命令行上。\)注意 `m_pMainWnd` 现在是类 `CWinThread` 的成员而不是 `CWinApp`。  
  
## 请参阅  
 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档模板创建](../mfc/document-template-creation.md)   
 [文档\/视图创建](../mfc/document-view-creation.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)