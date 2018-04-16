---
title: "派生的窗口类 |Microsoft 文档"
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
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4601a04932f467be3b63527f12c46f797d9e11d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="derived-window-classes"></a>派生的窗口类
你可以创建直接从 windows [CWnd](../mfc/reference/cwnd-class.md)，或其派生新的窗口类`CWnd`。 这是通常在如何创建你自己的自定义 windows。 但是，大多数窗口框架程序中使用而创建的一个`CWnd`-派生 MFC 提供的框架窗口类。  
  
## <a name="frame-window-classes"></a>框架窗口类  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 用于框架单个文档和其视图的 SDI 框架窗口。 框架窗口是应用程序的主框架窗口和当前文档的框架窗口。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 对于 MDI 应用程序用作主框架窗口。 主框架窗口是所有 MDI 文档窗口的容器，并与之共享的菜单栏。 MDI 框架窗口是出现在桌面上的顶级窗口。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 用于在 MDI 主框架窗口中打开的各个文档。 每个文档和其视图构造框架包含 MDI 主框架窗口的 MDI 子框架窗口。 MDI 子窗口非常类似于典型的框架窗口，但包含在 MDI 框架窗口而不是位于在桌面上。 但是，MDI 子窗口缺少自己的菜单栏，并且必须共享包含它的 MDI 框架窗口的菜单栏。  
  
 有关详细信息，请参阅[框架窗口](../mfc/frame-windows.md)。  
  
## <a name="other-window-classes-derived-from-cwnd"></a>从 CWnd 派生其他窗口类  
 除了框架窗口的 windows 的几个其他主要类别派生自`CWnd`:  
  
 *视图*  
 使用创建视图`CWnd`-派生类[CView](../mfc/reference/cview-class.md) （或其派生类之一）。 视图附加到文档并充当文档和用户之间的中介。 视图是通常填充 SDI 框架窗口或 MDI 子框架窗口 （或不受工具栏和/或状态栏的客户端区域的部分） 的客户端区域的子窗口 （而不是 MDI 子）。  
  
 *对话框*  
 使用创建对话框`CWnd`-派生类[CDialog](../mfc/reference/cdialog-class.md)。  
  
 *窗体*  
 创建窗体视图基于对话框模板资源，例如对话框框中，使用类[CFormView](../mfc/reference/cformview-class.md)， [CRecordView](../mfc/reference/crecordview-class.md)，或[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)。  
  
 *控件*  
 如按钮、 列表框和组合框控件使用其他类派生自创建`CWnd`。 请参阅[控制主题](../mfc/controls-mfc.md)。  
  
 *控件条*  
 包含控件的子窗口。 示例包括工具栏和状态栏。 请参阅[控件条](../mfc/control-bars.md)。  
  
## <a name="window-class-hierarchy"></a>窗口类层次结构  
 请参阅[MFC 层次结构图表](../mfc/hierarchy-chart.md)中*MFC 参考*。 中解释了视图[文档/视图体系结构](../mfc/document-view-architecture.md)。 中解释了对话框[对话框](../mfc/dialog-boxes.md)。  
  
## <a name="creating-your-own-special-purpose-window-classes"></a>创建您自己的特殊用途窗口类  
 除了由类库提供的窗口类，你可能需要特殊用途子窗口。 若要创建这样一个窗口，创建你自己[CWnd](../mfc/reference/cwnd-class.md)-派生类并将其设为帧或视图的子窗口。 请记住框架管理文档框架窗口的工作区的范围。 大部分的工作区由视图，但其他窗口，如控件条或你自己的自定义 windows，可能会共享空间与视图。 可能需要进行交互的类中的机制[CView](../mfc/reference/cview-class.md)和[CControlBar](../mfc/reference/ccontrolbar-class.md)定位在框架窗口的工作区中的子窗口。  
  
 [创建 Windows](../mfc/creating-windows.md)讨论创建窗口对象和他们管理的 windows。  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

