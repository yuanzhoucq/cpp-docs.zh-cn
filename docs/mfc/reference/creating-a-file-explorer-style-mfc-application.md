---
title: "创建文件资源管理器样式的 MFC 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcexplorer.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "浏览器, 资源管理器样式的应用程序"
  - "资源管理器样式的应用程序, 创建"
  - "MFC 应用程序, Windows 资源管理器样式"
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 创建文件资源管理器样式的 MFC 应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

许多 Windows 系统应用于文件资源管理器使用用户界面 \(UI\) \(UI\)。  例如，当开始时，文件 Explorer 看到一个垂直拆分条分割的应用程序划分工作区中。  工作区的左边提供导航和浏览功能，工作区的右边显示与左窗格中的选定内容相关的详细信息。  用户单击左窗格中的某项时，应用程序重新填充右窗格。  在 MDI 应用程序中，可以使用**“视图”**菜单中的命令更改右窗格显示的详细信息量。（在 SDI 或多顶级文档应用程序中，只能使用工具栏按钮更改详细信息。）  
  
 窗格的内容取决于应用程序。  在文件系统浏览器中，左窗格显示目录或计算机（或计算机组）的分层视图，而右窗格显示文件夹、个别的文件或计算机以及有关它们的详细信息。  这些内容不一定非是文件。  它们可以是电子邮件、错误报告或是数据库中的其他项。  
  
 向导为您创建了以下类：  
  
-   **CLeftView** 类定义工作区的左窗格。  通常是从 [CTreeView](../../mfc/reference/ctreeview-class.md) 导出。  
  
-   C*ProjName*View 类定义工作区的右窗格。  默认情况下，它从 [CListView](../../mfc/reference/clistview-class.md) 导出，但根据在向导的[生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页中的“基类”列表中指定的类，它可以是另一种视图类型。  
  
 生成的应用程序可以具有单文档界面 \(SDI\)、多文档界面 \(MDI\) 或多顶级文档结构。  应用程序创建的每个框架窗口都用 [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) 垂直拆分。  该应用程序的编码类似于使用拆分器的标准 MFC 应用程序的编码，不同的是该应用程序类型的每个拆分器窗格中都有单独的控件视图。  
  
 如果在右窗格中使用默认的列表视图，向导将创建附加的菜单选项（仅在 MDI 应用程序中）和工具栏按钮，以在大图标、小图标、列表和详细信息模式间切换视图的样式。  
  
### 开始创建文件资源管理器样式的 MFC 可执行文件  
  
1.  按照[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)中的指导操作。  
  
2.  在 MFC 应用程序向导的 [应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md) 页中，为 **文件资源管理器** 项目选择样式。  
  
3.  在其他向导页中设置所需的任何其他选项。  
  
4.  单击“完成”生成主干应用程序。  
  
 有关详细信息，请参阅：  
  
-   [多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [派生的视图类](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [应用程序设计选择](../../mfc/application-design-choices.md)  
  
## 请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [创建基于窗体的 MFC 应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)