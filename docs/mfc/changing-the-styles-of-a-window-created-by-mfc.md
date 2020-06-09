---
title: 更改 MFC 创建的窗口的样式
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: f3fd9f83112737e944d83cf00da685d81fe8b2a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624953"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>更改 MFC 创建的窗口的样式

在其功能版本中 `WinMain` ，MFC 注册多个标准窗口类。 由于你通常不会编辑 MFC `WinMain` ，因此该函数使你无机会更改 mfc 默认窗口样式。 本文介绍如何在现有应用程序中更改此类预先注册窗口类的样式。

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>更改新 MFC 应用程序中的样式

如果使用 Visual C++ 2.0 或更高版本，则在创建应用程序时，可以在应用程序向导中更改默认的窗口样式。 在应用程序向导的 "用户界面功能" 页中，您可以更改主框架窗口和 MDI 子窗口的样式。 对于任一窗口类型，都可以指定其框架粗细（厚或细）以及以下任何内容：

- 窗口是否具有最小化或最大化控件。

- 窗口最初显示时是最小化、最大化还是两者都不显示。

对于主框架窗口，还可以指定窗口是否包含系统菜单。 对于 MDI 子窗口，可以指定窗口是否支持拆分窗格。

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>更改现有应用程序中的样式

如果要更改现有应用程序中的窗口属性，请改为按照本文其余部分中的说明进行操作。

若要更改使用应用程序向导创建的框架应用程序所使用的默认窗口属性，请重写窗口的[PreCreateWindow](reference/cwnd-class.md#precreatewindow)虚拟成员函数。 `PreCreateWindow`允许应用程序访问通常由[CDocTemplate](reference/cdoctemplate-class.md)类在内部管理的创建过程。 框架 `PreCreateWindow` 只需在创建窗口之前调用。 通过修改传递到的[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)结构 `PreCreateWindow` ，你的应用程序可以更改用于创建窗口的属性。 例如，若要确保窗口不使用标题，请使用以下按位运算：

[!code-cpp[NVC_MFCDocView#15](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../overview/visual-cpp-samples.md)示例应用程序演示了这种更改窗口特性的方法。 根据应用程序在中所做的更改 `PreCreateWindow` ，可能需要调用函数的基类实现。

以下讨论涉及到 SDI 事例和[MDI 情况](#_core_the_mdi_case)。

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>SDI Case

在单文档界面（SDI）应用程序中，框架中的默认窗口样式是**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**样式的组合。 **FWS_ADDTOTITLE**是一种特定于 MFC 的样式，指示框架将文档标题添加到窗口的标题。 若要在 SDI 应用程序中更改窗口属性，请重写 `PreCreateWindow` 派生自的类 `CFrameWnd` （应用程序向导名称）中的函数 `CMainFrame` 。 例如：

[!code-cpp[NVC_MFCDocViewSDI#11](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

此代码将创建一个主框架窗口，其中不会最小化和最大化按钮，且没有可调边框。 窗口最初在屏幕上居中。

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>MDI Case

在多文档界面（MDI）应用程序中更改子窗口的窗口样式需要执行一些其他操作。 默认情况下，使用应用程序向导创建的 MDI 应用程序使用 MFC 中定义的默认[CMDIChildWnd](reference/cmdichildwnd-class.md)类。 若要更改 MDI 子窗口的窗口样式，必须从派生新类，并将 `CMDIChildWnd` 项目中对的所有引用替换为 `CMDIChildWnd` 对新类的引用。 最可能的情况是，对 `CMDIChildWnd` 应用程序中的唯一引用位于应用程序的 `InitInstance` 成员函数中。

MDI 应用程序中使用的默认窗口样式是**WS_CHILD**、 **WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**样式的组合。 若要更改 MDI 应用程序的子窗口的窗口特性，请重写派生自的类中的[PreCreateWindow](reference/cwnd-class.md#precreatewindow)函数 `CMDIChildWnd` 。 例如：

[!code-cpp[NVC_MFCDocView#16](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

此代码将创建不带 "最大化" 按钮的 MDI 子窗口。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [Windows 样式](reference/styles-used-by-mfc.md#window-styles)

- [框架窗口样式](frame-window-styles-cpp.md)

- [窗口样式](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>另请参阅

[框架窗口样式](frame-window-styles-cpp.md)
