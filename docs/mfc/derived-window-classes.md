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
ms.openlocfilehash: bf0d8e82f1a1793f4e5561e24ed9ca173511d07c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462109"
---
# <a name="derived-window-classes"></a>派生的窗口类

您可以创建直接从 windows [CWnd](../mfc/reference/cwnd-class.md)，或派生新的窗口类从`CWnd`。 这是通常创建你自己的自定义 windows 的方式。 但是，在框架程序中使用的大多数窗口改为创建从之一`CWnd`-派生的 MFC 提供的框架窗口类。

## <a name="frame-window-classes"></a>框架窗口类

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
用于单个文档和其视图的帧的 SDI 框架窗口。 框架窗口是应用程序的主框架窗口和当前文档的框架窗口。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
作为主框架窗口用于 MDI 应用程序。 主框架窗口是所有 MDI 文档窗口的容器，并与之共享其菜单栏。 MDI 框架窗口是出现在桌面上的顶级窗口。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
用于在 MDI 主框架窗口中打开各个文档。 每个文档和其视图构造框架包含 MDI 主框架窗口的 MDI 子框架窗口。 MDI 子窗口非常类似于典型的框架窗口，但包含在 MDI 框架窗口而不是坐在桌面上内。 但是，MDI 子窗口缺少其自己的菜单栏，并且必须共享包含它的 MDI 框架窗口的菜单栏。

有关详细信息，请参阅[帧 Windows](../mfc/frame-windows.md)。

## <a name="other-window-classes-derived-from-cwnd"></a>从 CWnd 派生的其他窗口类

除了框架窗口的 windows 的多个其他主要类别派生自`CWnd`:

*视图*<br/>
使用创建视图`CWnd`的派生类[CView](../mfc/reference/cview-class.md) （或其派生类之一）。 一个视图附加到文档，并充当该文档与用户之间的中介。 视图是填充 SDI 框架窗口或 MDI 子框架窗口 （或不受工具栏和/或状态栏的客户端区域的部分） 的客户端区域，通常的子窗口 （不 MDI 子窗体）。

*对话框*<br/>
使用创建对话框`CWnd`的派生类[CDialog](../mfc/reference/cdialog-class.md)。

*窗体*<br/>
使用类创建窗体视图基于对话框模板资源，例如对话框框中， [CFormView](../mfc/reference/cformview-class.md)， [CRecordView](../mfc/reference/crecordview-class.md)，或[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)。

*控件*<br/>
创建按钮、 列表框和组合框等控件使用的其他类派生自`CWnd`。 请参阅[控制主题](../mfc/controls-mfc.md)。

*控件条*<br/>
包含控件的子窗口。 示例包括工具栏和状态栏。 请参阅[控件条](../mfc/control-bars.md)。

## <a name="window-class-hierarchy"></a>窗口类层次结构

请参阅[MFC 层次结构图表](../mfc/hierarchy-chart.md)中*MFC 参考*。 中介绍了视图[文档/视图体系结构](../mfc/document-view-architecture.md)。 中介绍了对话框[对话框](../mfc/dialog-boxes.md)。

## <a name="creating-your-own-special-purpose-window-classes"></a>创建您自己的专用的窗口类

除了由类库提供的窗口类，您可能需要专用的子窗口。 若要创建此类窗口，创建您自己[CWnd](../mfc/reference/cwnd-class.md)-派生的类，并使其框架或视图的子窗口。 请记住框架管理文档框架窗口的工作区的范围。 大部分客户端区域由一个视图，但其他窗口，如控件条或你自己的自定义 windows，可能会共享空间与视图。 可能需要与类中的机制进行交互[CView](../mfc/reference/cview-class.md)并[CControlBar](../mfc/reference/ccontrolbar-class.md)用于在框架窗口的工作区中定位子窗口。

[创建 Windows](../mfc/creating-windows.md)讨论创建窗口对象和他们管理的 windows。

## <a name="see-also"></a>请参阅

[窗口对象](../mfc/window-objects.md)

