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
ms.openlocfilehash: c8a3a5d9b8b007887dfb31f7459c0269377b38fd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294156"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>更改 MFC 创建的窗口的样式

在其版本中的`WinMain`函数，MFC 将为您注册若干标准窗口类。 由于你通常不编辑 MFC 的`WinMain`，该函数为你提供了没有机会更改 MFC 默认窗口样式。 本文介绍如何更改现有应用程序中的此类的预先注册的窗口类样式。

##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> 在新的 MFC 应用程序中更改样式

如果你使用 Visual c + + 2.0 或更高版本，你可以创建你的应用程序时更改应用程序向导中的默认窗口样式。 在应用程序向导的用户界面功能页上，可以更改主框架窗口和 MDI 子窗口的样式。 对于任一窗口类型，您可以指定其帧粗细 （胖或瘦） 和任何以下：

- 窗口是否具有最小化或最大化控件。

- 是否该窗口将显示最初最小化、 最大化，或都不。

对于主框架窗口，您还可以指定窗口是否具有系统菜单。 对于 MDI 子窗口，可以指定窗口是否支持拆分器窗格。

##  <a name="_core_changing_styles_in_an_existing_application"></a> 更改现有应用程序中的样式

如果您要更改窗口特性中现有的应用程序，而是按照在本文的其余部分中的说明。

若要更改使用的框架应用程序使用应用程序向导创建的默认窗口属性，请重写窗口的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)虚拟成员函数。 `PreCreateWindow` 允许应用程序访问通常由在内部管理的创建过程[CDocTemplate](../mfc/reference/cdoctemplate-class.md)类。 框架将调用`PreCreateWindow`之前创建窗口。 通过修改[CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa)结构传递给`PreCreateWindow`，你的应用程序可以更改用来创建窗口的属性。 例如，若要确保一个窗口不使用标题，请使用以下的按位运算：

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../visual-cpp-samples.md)示例应用程序演示了此更改窗口特性的方法。 具体取决于你的应用程序中的更改`PreCreateWindow`，可能会需要调用该函数的基类实现。

以下讨论涵盖了 SDI 用例和[MDI 用例](#_core_the_mdi_case)。

##  <a name="_core_the_sdi_case"></a> SDI 用例

在单文档界面 (SDI) 应用程序中，该框架的默认窗口样式是的组合**WS_OVERLAPPEDWINDOW**并**FWS_ADDTOTITLE**样式。 **FWS_ADDTOTITLE**是指示要添加到窗口的标题文档标题的框架的特定于 MFC 的样式。 若要更改窗口特性 SDI 应用程序中的，重写`PreCreateWindow`函数在类中的派生自`CFrameWnd`(该应用程序向导名称`CMainFrame`)。 例如：

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

此代码将创建主框架窗口而不需要最小化和最大化按钮并可调整大小的边框。 窗口最初是在屏幕上居中显示。

##  <a name="_core_the_mdi_case"></a> MDI 用例

一些额外工作，需要更改处于多文档界面 (MDI) 应用程序的子窗口的窗口样式。 默认情况下使用应用程序向导创建的 MDI 应用程序使用默认值[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)在 MFC 中定义的类。 若要更改的 MDI 子窗口的窗口样式，您必须派生新类从`CMDIChildWnd`替换为对所有引用和`CMDIChildWnd`项目中包含的对新的类的引用。 很可能对的唯一引用`CMDIChildWnd`应用程序中位于应用程序的`InitInstance`成员函数。

在 MDI 应用程序中使用的默认窗口样式是的组合**WS_CHILD**， **WS_OVERLAPPEDWINDOW**，并**FWS_ADDTOTITLE**样式。 若要更改的 MDI 应用程序的子窗口的窗口属性，请重写[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)函数在类中的派生自`CMDIChildWnd`。 例如：

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

此代码创建 MDI 子窗口，没有最大化按钮。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [Windows 样式](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [框架窗口样式](../mfc/frame-window-styles-cpp.md)

- [窗口样式](/windows/desktop/winmsg/window-styles)

## <a name="see-also"></a>请参阅

[框架窗口样式](../mfc/frame-window-styles-cpp.md)
