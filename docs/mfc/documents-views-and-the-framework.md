---
title: 文档、视图和框架
ms.date: 11/19/2018
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 17956c0b175e978c6e4e2fefcdad5f744929d457
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621837"
---
# <a name="documents-views-and-the-framework"></a>文档、视图和框架

MFC 框架的核心是文档和视图的概念。 文档是用户在编辑会话中与之进行交互的数据对象。 它是通过 "**文件**" 菜单上的 "**新建**" 或 "**打开**" 命令创建的，通常保存在文件中。 （从类派生的标准 MFC 文档 `CDocument` 不同于活动文档和 OLE 复合文档。）视图是一个窗口对象，用户通过该对象与文档交互。

一个正在运行的应用程序中的关键对象有：

- 一个文档或多个文档。

   文档类（派生自[CDocument](reference/cdocument-class.md)）指定应用程序的数据。

   如果希望在应用程序中进行 OLE 功能，请根据所需的功能类型，从[COleDocument](reference/coledocument-class.md)或其派生类之一派生文档类。

- 一个视图或多个视图。

   视图类（派生自[CView](reference/cview-class.md)）是用户的 "数据窗口"。 视图类控制用户查看文档的数据并与之交互的方式。 在某些情况下，您可能希望一个文档拥有多个数据视图。

   如果需要滚动，请从[CScrollView](reference/cscrollview-class.md)派生。 如果视图有一个在对话框模板资源中布局的用户界面，请从[CFormView](reference/cformview-class.md)派生。 对于简单的文本数据，请使用或从[CEditView](reference/ceditview-class.md)派生。 对于基于窗体的数据访问应用程序（如数据输入程序），请从[CRecordView](reference/crecordview-class.md)派生（适用于 ODBC）。 还可用的类有[CTreeView](reference/ctreeview-class.md)、 [CListView](reference/clistview-class.md)和[CRichEditView](reference/cricheditview-class.md)类。

- 框架窗口

   视图显示在“文档框架窗口”中。 在 SDI 应用程序中，文档框架窗口也是应用程序的“主框架窗口”。 在 MDI 应用程序中，文档窗口是显示在主框架窗口中的子窗口。 派生的主框架窗口类指定包含您的视图的框架窗口的样式和其他特性。 如果需要自定义框架窗口，请从[CFrameWnd](reference/cframewnd-class.md)派生以自定义用于 SDI 应用程序的文档框架窗口。 从[CMDIFrameWnd](reference/cmdiframewnd-class.md)派生以自定义 MDI 应用程序的主框架窗口。 还从[CMDIChildWnd](reference/cmdichildwnd-class.md)派生一个类，以自定义应用程序支持的每种不同类型的 MDI 文档框架窗口。

- 一个或多个文档模板

   文档模板可协调文档、视图和框架窗口的创建。 从类[CDocTemplate](reference/cdoctemplate-class.md)派生的特定文档模板类创建和管理一种类型的所有打开的文档。 支持多种文档类型的应用程序具有多个文档模板。 将类[CSingleDocTemplate](reference/csingledoctemplate-class.md)用于 SDI 应用程序，或将类[CMultiDocTemplate](reference/cmultidoctemplate-class.md)用于 MDI 应用程序。

- 应用程序对象

   应用程序类（派生自[CWinApp](reference/cwinapp-class.md)）控制以上所有对象，并指定应用程序行为，如初始化和清理。 应用程序仅有的一个应用程序对象为应用程序支持的任何文档类型创建和管理文档模板。

- 线程对象

   如果你的应用程序创建了单独的执行线程（例如，在后台执行计算），则将使用派生自[CWinThread](reference/cwinthread-class.md)的类。 [CWinApp](reference/cwinapp-class.md)本身派生自 `CWinThread` ，它表示应用程序中的主执行线程（或主进程）。 还可以在辅助线程中使用 MFC。

在一个正在运行的应用程序中，这些对象以协作方式响应用户操作（由命令和其他消息绑定在一起）。 一个应用程序对象管理一个或多个文档模板。 每个文档模板创建并管理一个或多个文档（具体取决于应用程序是 SDI 还是 MDI）。 用户通过包含在框架窗口中的视图查看和操作文档。 下图演示了 SDI 应用程序的这些对象之间的关系。

![正在运行的 SDI 应用程序中的对象](../mfc/media/vc386v1.gif "正在运行的 SDI 应用程序中的对象") <br/>
运行 SDI 应用程序中的对象

本系列文章的其他部分介绍了框架工具、MFC 应用程序向导和资源编辑器如何创建这些对象，如何协同工作以及如何在编程中使用它们。 [窗口对象](window-objects.md)和[文档/视图体系结构](document-view-architecture.md)中更详细地讨论了文档、视图和框架窗口。

## <a name="see-also"></a>另请参阅

[使用类编写适用于 Windows 的应用程序](using-the-classes-to-write-applications-for-windows.md)
