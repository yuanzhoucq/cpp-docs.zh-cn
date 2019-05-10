---
title: 工具栏基础知识
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: 9c784db2e1a482b313147e6837d6bbbd16d0ecb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168214"
---
# <a name="toolbar-fundamentals"></a>工具栏基础知识

本指南介绍了基本的 MFC 实现，允许你通过应用程序向导中选择一个选项将默认工具栏添加到你的应用程序。 涵盖的主题包括：

- [应用程序向导工具栏选项](#_core_the_appwizard_toolbar_option)

- [代码中的工具栏](#_core_the_toolbar_in_code)

- [编辑工具栏资源](#_core_editing_the_toolbar_resource)

- [多个工具栏](#_core_multiple_toolbars)

##  <a name="_core_the_appwizard_toolbar_option"></a> 应用程序向导工具栏选项

若要获取带有默认按钮的一个工具栏，请选择标记为用户界面功能页上的标准停靠工具栏选项。 这将代码添加到你的应用程序的：

- 创建工具栏对象。

- 管理包括其功能以停靠或浮动工具栏。

##  <a name="_core_the_toolbar_in_code"></a> 代码中的工具栏

工具栏[CToolBar](../mfc/reference/ctoolbar-class.md)对象声明的应用程序的数据成员为`CMainFrame`类。 换而言之，在主框架窗口对象中嵌入工具栏对象。 这意味着，MFC 创建工具栏时它会创建框架窗口并销毁工具栏在销毁框架窗口。 下面的分部类声明，为多文档界面 (MDI) 应用程序显示嵌入式的工具栏和嵌入的状态栏的数据成员。 它还演示了重写`OnCreate`成员函数。

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

工具栏创建发生在`CMainFrame::OnCreate`。 MFC 调用[OnCreate](../mfc/reference/cwnd-class.md#oncreate)后创建的窗口框架，但它变得可见之前。 默认值`OnCreate`应用程序向导生成执行以下工具栏任务：

1. 调用`CToolBar`对象的[创建](../mfc/reference/ctoolbar-class.md#create)成员函数来创建基础[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。

1. 调用[LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)加载工具栏资源信息。

1. 调用函数，可以让停靠、 浮动和工具提示。 有关这些调用的详细信息，请参阅文章[停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)。

> [!NOTE]
>  MFC 常规示例[DOCKTOOL](../overview/visual-cpp-samples.md)包括旧的和新 MFC 工具栏的说明。 使用工具栏`COldToolbar`需要在步骤 2 中的调用`LoadBitmap`(而非`LoadToolBar`) 和`SetButtons`。 新的工具栏要求对调用`LoadToolBar`。

停靠、 浮动和工具提示的调用是可选的。 您可以删除这些行从`OnCreate`您的喜好而定。 结果是保持固定，不能浮动或重新停靠并不能显示工具提示的工具栏。

##  <a name="_core_editing_the_toolbar_resource"></a> 编辑工具栏资源

获取与应用程序向导的默认工具栏基于**RT_TOOLBAR** MFC 4.0 版中引入的自定义资源。 您可以编辑与此资源[工具栏编辑器](../windows/toolbar-editor.md)。 编辑器允许您轻松地添加、 删除和重新排列按钮。 它包含与视觉对象中的常规图形编辑器非常相似的按钮的图形编辑器C++。 如果编辑视觉对象的以前版本中的工具栏C++，您会发现任务更容易现在。

若要连接到命令工具栏按钮，您为该按钮的命令 ID，如`ID_MYCOMMAND`。 在编辑器工具栏按钮的属性页中指定的命令 ID。 然后，创建命令的处理程序函数 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)有关详细信息)。

新[CToolBar](../mfc/reference/ctoolbar-class.md)成员函数处理**RT_TOOLBAR**资源。 [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)已经取代[LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap)若要加载的工具栏按钮图像、 位图和[SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons)设置按钮样式和连接与位图图像的按钮。

有关使用工具栏编辑器的详细信息，请参阅[工具栏编辑器](../windows/toolbar-editor.md)。

##  <a name="_core_multiple_toolbars"></a> 多个工具栏

应用程序向导为您提供一个默认的工具栏。 如果在应用程序中需要多个工具栏，可以建模您的代码为默认工具栏向导生成的代码所基于的其他工具栏。

如果你想要作为命令的结果显示一个工具栏，你将需要：

- 使用工具栏编辑器创建新的工具栏资源并将其在加载`OnCreate`与[LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar)成员函数。

- 嵌入的新[CToolBar](../mfc/reference/ctoolbar-class.md)在主框架窗口类中的对象。

- 进行中的相应函数调用`OnCreate`停靠或浮动工具栏、 设置其样式中，依次类推。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [MFC 工具栏实现 （在工具栏上的概述信息）](../mfc/mfc-toolbar-implementation.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)并[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

- [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)

- [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
