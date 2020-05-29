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
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373477"
---
# <a name="toolbar-fundamentals"></a>工具栏基础知识

本文介绍了通过选择应用程序向导中的选项向应用程序添加默认工具栏的基本 MFC 实现。 涵盖的主题包括：

- ["应用程序向导"工具栏选项](#_core_the_appwizard_toolbar_option)

- [代码中的工具栏](#_core_the_toolbar_in_code)

- [编辑工具栏资源](#_core_editing_the_toolbar_resource)

- [多个工具栏](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>应用程序向导工具栏选项

要获取带有默认按钮的单个工具栏，请在标记为"用户界面功能"的页面上选择"标准停靠"工具栏选项。 这会向应用程序添加代码：

- 创建工具栏对象。

- 管理工具栏，包括其停靠或浮动的能力。

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>代码中的工具栏

工具栏是[CToolBar](../mfc/reference/ctoolbar-class.md)对象，声明为应用程序`CMainFrame`类的数据成员。 换句话说，工具栏对象嵌入在主框架窗口对象中。 这意味着 MFC 在创建框架窗口时创建工具栏，并在破坏框架窗口时销毁工具栏。 以下部分类声明（对于多个文档接口 （MDI） 应用程序）显示嵌入工具栏和嵌入状态栏的数据成员。 它还显示成员函数的`OnCreate`重写。

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

工具栏创建发生在 中`CMainFrame::OnCreate`。 MFC 在为框架创建窗口后，但在其变为可见之前调用[OnCreate。](../mfc/reference/cwnd-class.md#oncreate) 应用程序向导`OnCreate`生成的默认值执行以下工具栏任务：

1. 调用`CToolBar`对象的["创建](../mfc/reference/ctoolbar-class.md#create)成员"函数以创建基础[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。

1. 调用[LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)以加载工具栏资源信息。

1. 调用函数以启用停靠、浮动和工具提示。 有关这些调用的详细信息，请参阅文章["停靠"和"浮动工具栏](../mfc/docking-and-floating-toolbars.md)"。

> [!NOTE]
> MFC 一般示例[DOCKTOOL](../overview/visual-cpp-samples.md)包括新旧 MFC 工具栏的插图。 使用的`COldToolbar`工具栏需要步骤 2 中的调用`LoadBitmap`（而不是`LoadToolBar`） 和`SetButtons`调用 。 新的工具栏需要调用`LoadToolBar`。

停靠、浮动和工具提示调用是可选的。 `OnCreate`如果您愿意，可以从中删除这些行。 结果是工具栏保持固定、无法浮动或重新停靠以及无法显示工具提示。

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>编辑工具栏资源

使用应用程序向导获取的默认工具栏基于 mFC 版本 4.0 中介绍**的RT_TOOLBAR**自定义资源。 您可以使用[工具栏编辑器](../windows/toolbar-editor.md)编辑此资源。 编辑器可让您轻松添加、删除和重新排列按钮。 它包含与 Visual C++ 中的一般图形编辑器非常相似的按钮的图形编辑器。 如果您在早期版本的 Visual C++ 中编辑了工具栏，则现在将发现该任务要容易得多。

要将工具栏按钮连接到命令，请为该按钮提供命令 ID，如`ID_MYCOMMAND`。 在工具栏编辑器中指定按钮的属性页中的命令 ID。 然后为命令创建处理程序函数（有关详细信息，请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

新的[CToolBar](../mfc/reference/ctoolbar-class.md)成员函数使用**RT_TOOLBAR**资源。 [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)现在取代[LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap)来加载工具栏按钮图像的位图，[然后设置 Button](../mfc/reference/ctoolbar-class.md#setbuttons)来设置按钮样式，并连接带有位图图像的按钮。

有关使用工具栏编辑器的详细信息，请参阅[工具栏编辑器](../windows/toolbar-editor.md)。

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>多个工具栏

应用程序向导为您提供一个默认工具栏。 如果应用程序中需要多个工具栏，则可以根据默认工具栏的向导生成的代码为其他工具栏建模代码。

如果要将工具栏显示为命令的结果，则需要：

- 使用工具栏编辑器创建新工具栏资源，然后`OnCreate`使用[LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar)成员函数加载它。

- 在主框架窗口类中嵌入新的[CToolBar](../mfc/reference/ctoolbar-class.md)对象。

- 进行适当的函数调用以`OnCreate`停靠或浮动工具栏、设置其样式等。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [MFC 工具栏实现（工具栏概述信息）](../mfc/mfc-toolbar-implementation.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

- [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)

- [使用旧工具栏](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
