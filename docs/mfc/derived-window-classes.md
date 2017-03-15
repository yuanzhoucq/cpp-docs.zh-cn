---
title: "派生的窗口类 | Microsoft Docs"
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
  - "类 [C++], 派生"
  - "CWnd 类, 类派生自"
  - "派生类, 窗口类"
  - "层次结构, 窗口类"
  - "窗口类层次结构"
  - "窗口类, 派生"
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 派生的窗口类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以创建 windows 直接从 [CWnd](../mfc/reference/cwnd-class.md)，或者从 `CWnd`派生新窗口选件类。  这是如何创建自己的自定义窗口。  但是，用于帧计划的大多数 windows 从一个 `CWnd`\- MFC 提供的派生框架窗口选件类创建的。  
  
## 框架窗口类  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 用于 SDI 帧单个文档框架窗口及其视图。  框架窗口是应用程序的主框架窗口，并且框架窗口当前文件。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 用作主框架窗口在 MDI 应用程序。  主框架窗口是所有 MDI 的容器文档窗口和共享其与它们的菜单栏。  MDI 框架窗口是在桌面上的顶级窗口。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 用于单个在 MDI 主框架窗口文档打开。  每个文档及其视图由 MDI 主框架窗口中包含的 MDI 子框架窗口配置。  MDI子窗口看起来更像一个典型的框架窗口，但它包含一个MDI框架窗口而不是桌面。  但是，MDI 子窗口没有自己的菜单栏并且必须共享包含它的 MDI 框架窗口的菜单栏。  
  
 有关更多信息，请参见[Frame Windows](../mfc/frame-windows.md) 。  
  
## 从 CWnd 派生的其他窗口选件类  
 除了框架窗口外，窗口还有其他一些主要类别 `CWnd`从派生：  
  
 *视图*  
 视图创建使用 `CWnd`派生类及其派生类 [CView](../mfc/reference/cview-class.md) \(或其中一个派生类\)。  视图附加到文档并为文档和用户之间的中间方。  视图是窗口的子窗口 \(不是 MDI 子窗体\)通常加载 SDI 框架窗口客户端区域或 MDI 子框架窗口 \(或工具栏和状态栏中未包含的客户端区域的该部分\)。  
  
 *对话框*  
 使用 `CWnd`派生类 [CDialog](../mfc/reference/cdialog-class.md)创建对话框。  
  
 *窗体*  
 使用选件类 [CFormView](../mfc/reference/cformview-class.md)、[CRecordView](../mfc/reference/crecordview-class.md)或 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)，从而基于对话框模板资源的视图 ，例如，对话框，创建。  
  
 *控件*  
 控件 ，例如，按钮、列表框，并且，组合框创建使用从 `CWnd`派生的其他选件类。  参见[控件主题](../mfc/controls-mfc.md)。  
  
 *控件条*  
 包含控件的子窗口。  示例包括工具栏和状态栏。  参见[控制条](../mfc/control-bars.md)。  
  
## 窗口类层次结构  
 请参见" MFC 参考"中 *的*[MFC 层次结构图](../mfc/hierarchy-chart.md) 。  视图在 [文档\/视图结构](../mfc/document-view-architecture.md)中被解释。  对话框在 [对话框](../mfc/dialog-boxes.md)中被解释。  
  
## 创建您的专用窗口选件类  
 除了选件类库提供的 windows 选件类之外，您可能需要私有子窗口。  若要创建此类窗口，请创建您的 [CWnd](../mfc/reference/cwnd-class.md)派生类并使其成为子窗口框架或试图。  记住框架管理文档框架窗口的客户端区域的区域。  大多数客户端区域由视图管理，但是，其他窗口，例如控件条或您的自定义窗口，可以使用视图共享空间。  您在框架窗口的客户端区域可能需要在选件类 [CView](../mfc/reference/cview-class.md) 和 [CControlBar](../mfc/reference/ccontrolbar-class.md) 的结构交互确定的子窗口。  
  
 这些托管[创建窗口](../mfc/creating-windows.md) 讨论 windows 对象的创建和窗口。  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)