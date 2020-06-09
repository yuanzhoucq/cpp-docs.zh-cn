---
title: 派生的窗口类
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: c84284b765e740fa0a13972e9902e7737e15bbab
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623176"
---
# <a name="derived-window-classes"></a>派生的窗口类

可以直接从[CWnd](reference/cwnd-class.md)创建 windows，或从派生新的窗口类 `CWnd` 。 通常，这是创建自己的自定义窗口的方式。 但是，框架程序中使用的大多数 windows 都是 `CWnd` 通过 MFC 提供的一个派生的框架窗口类创建的。

## <a name="frame-window-classes"></a>框架窗口类

[CFrameWnd](reference/cframewnd-class.md)<br/>
用于 SDI 框架窗口，该窗口框架是单个文档及其视图。 框架窗口既是应用程序的主框架窗口，也是当前文档的框架窗口。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
用作 MDI 应用程序的主框架窗口。 主框架窗口是所有 MDI 文档窗口的容器，并与其共享其菜单栏。 MDI 框架窗口是显示在桌面上的顶级窗口。

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
用于在 MDI 主框架窗口中打开的单个文档。 每个文档及其视图都通过 MDI 主框架窗口中包含的 MDI 子框架窗口进行分帧。 MDI 子窗口的外观非常类似于典型的框架窗口，但包含在 MDI 框架窗口中，而不是放在桌面上。 但是，MDI 子窗口缺少自己的菜单栏，必须共享包含它的 MDI 框架窗口的菜单栏。

有关详细信息，请参阅[框架窗口](frame-windows.md)。

## <a name="other-window-classes-derived-from-cwnd"></a>其他从 CWnd 派生的窗口类

除了框架窗口之外，还有其他几种主要类别的 windows 派生自 `CWnd` ：

*视图*<br/>
视图使用 `CWnd` 派生类[CView](reference/cview-class.md) （或它的派生类之一）创建。 视图附加到文档并充当文档和用户之间的中介。 视图是通常填充 SDI 框架窗口或 MDI 子框架窗口（或工具栏和/或状态栏未涵盖的客户端区域的工作区）的工作区的子窗口（而非 MDI 子窗口）。

*对话框*<br/>
使用 `CWnd` 派生类[CDialog](reference/cdialog-class.md)创建对话框。

*窗体*<br/>
基于对话框模板资源的窗体视图，如对话框，是使用[CFormView](reference/cformview-class.md)、 [CRecordView](reference/crecordview-class.md)或[CDaoRecordView](reference/cdaorecordview-class.md)类创建的。

*控件*<br/>
控件（如按钮、列表框和组合框）是使用派生自的其他类创建的 `CWnd` 。 请参阅[控件主题](controls-mfc.md)。

*控件条*<br/>
包含控件的子窗口。 示例包括工具栏和状态栏。 请参阅[控件条](control-bars.md)。

## <a name="window-class-hierarchy"></a>窗口类层次结构

请参阅*Mfc 参考*中的[mfc 层次结构图](hierarchy-chart.md)。 视图在[文档/视图体系结构](document-view-architecture.md)中介绍。 对话框中介绍了对话框[。](dialog-boxes.md)

## <a name="creating-your-own-special-purpose-window-classes"></a>创建自己的专用窗口类

除了类库提供的窗口类之外，您可能还需要专门的子窗口。 若要创建此类窗口，请创建自己的[CWnd](reference/cwnd-class.md)派生类，并使其成为框架或视图的子窗口。 请记住，框架管理文档框架窗口的工作区的范围。 大多数工作区由视图管理，但其他窗口（如控件条或您自己的自定义窗口）可能与视图共享空间。 可能需要与类[CView](reference/cview-class.md)和[CControlBar](reference/ccontrolbar-class.md)中的机制交互，以便在框架窗口的工作区中定位子窗口。

[创建 Windows](creating-windows.md)讨论了窗口对象和它们所管理的窗口的创建。

## <a name="see-also"></a>另请参阅

[窗口对象](window-objects.md)
