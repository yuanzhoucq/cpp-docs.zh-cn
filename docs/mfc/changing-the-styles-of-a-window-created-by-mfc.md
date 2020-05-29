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
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374596"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>更改 MFC 创建的窗口的样式

在其版本的函数中`WinMain`，MFC 为您注册了几个标准窗口类。 由于您通常不编辑 MFC 的`WinMain`，因此该函数无法更改 MFC 默认窗口样式。 本文介绍如何更改现有应用程序中此类预先注册的窗口类的样式。

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>更改新 MFC 应用程序中的样式

如果您使用的是 Visual C++ 2.0 或更高版本，则可以在创建应用程序时更改应用程序向导中的默认窗口样式。 在应用程序向导的用户界面功能页中，您可以更改主框架窗口和 MDI 子窗口的样式。 对于任一窗口类型，您可以指定其帧厚度（厚或薄）和以下任一：

- 窗口是否具有最小化控件或最大化控件。

- 窗口最初是否出现最小化、最大化，或者两者均未出现。

对于主框架窗口，还可以指定窗口是否具有系统菜单。 对于 MDI 子窗口，可以指定窗口是否支持拆分器窗格。

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>更改现有应用程序中的样式

如果要更改现有应用程序中的窗口属性，请改用本文其余部分中的说明。

要更改使用应用程序向导创建的框架应用程序使用的默认窗口属性，请覆盖窗口的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)虚拟成员函数。 `PreCreateWindow`允许应用程序访问通常由[CDocTemplate](../mfc/reference/cdoctemplate-class.md)类在内部管理的创建过程。 框架在创建`PreCreateWindow`窗口之前调用。 通过修改传递给`PreCreateWindow`的[CREATETRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)结构，应用程序可以更改用于创建窗口的属性。 例如，为了确保窗口不使用标题，请使用以下位视操作：

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../overview/visual-cpp-samples.md)示例应用程序演示了此用于更改窗口属性的技术。 根据 应用程序在 中的`PreCreateWindow`更改，可能需要调用 函数的基类实现。

以下讨论包括SDI案和[MDI案](#_core_the_mdi_case)。

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>SDI 案例

在单个文档接口 （SDI） 应用程序中，框架中的默认窗口样式是**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**样式的组合。 **FWS_ADDTOTITLE**是特定于 MFC 的样式，用于指示框架将文档标题添加到窗口的标题中。 要更改 SDI 应用程序中的窗口属性，请重写类`PreCreateWindow`中派生自`CFrameWnd`的函数（应用程序向导名称`CMainFrame`）。 例如：

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

此代码创建一个主框架窗口，没有最小化和最大化按钮，并且没有相当大的边框。 窗口最初居中在屏幕上。

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>MDI 案例

在多个文档接口 （MDI） 应用程序中更改子窗口的窗口样式还需要多做一些工作。 默认情况下，使用应用程序向导创建的 MDI 应用程序使用在 MFC 中定义的默认[CMDIChildwnd](../mfc/reference/cmdichildwnd-class.md)类。 要更改 MDI 子窗口的窗口样式，必须从`CMDIChildWnd`项目中派生一个新类，并将对`CMDIChildWnd`项目中的所有引用替换为对新类的引用。 最有可能的是，应用程序中的唯一引用`CMDIChildWnd`位于应用程序`InitInstance`的成员函数中。

MDI 应用程序中使用的默认窗口样式是**WS_CHILD、WS_OVERLAPPEDWINDOW****和FWS_ADDTOTITLE**样式的组合**WS_OVERLAPPEDWINDOW**。 要更改 MDI 应用程序子窗口的窗口属性，请覆盖派生自 的`CMDIChildWnd`类中的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)函数。 例如：

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

此代码创建没有"最大化"按钮的 MDI 子窗口。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [框架窗口样式](../mfc/frame-window-styles-cpp.md)

- [窗口样式](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>另请参阅

[框架窗口样式](../mfc/frame-window-styles-cpp.md)
