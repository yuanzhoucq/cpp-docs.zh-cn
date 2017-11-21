---
title: "更改窗口样式创建的 MFC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7745054066a928c414360a215605cf343971ddf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>更改 MFC 创建的窗口的样式
它的版本中`WinMain`函数，MFC 为您注册若干标准窗口类。 由于你通常不编辑 MFC 的`WinMain`，，函数使您可以以后你无法更改 MFC 默认窗口样式。 此文章介绍了如何更改现有应用程序中的此类的预先注册的窗口类的样式。  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a>在新的 MFC 应用程序中更改样式  
 如果你使用 Visual c + + 2.0 或更高版本，你可以创建你的应用程序时更改应用程序向导中的默认窗口样式。 在应用程序向导的用户界面功能页上，你可以更改你的主框架窗口和 MDI 子窗口的样式。 对于任一窗口类型，你可以指定框架粗细 （厚或精简） 和以下任一：  
  
-   窗口是否具有最小化或最大化控件。  
  
-   是否显示该窗口最初最小化，最大化时，或都不。  
  
 对于主框架窗口，你还可以指定窗口是否具有系统菜单。 对于 MDI 子窗口，你可以指定窗口是否支持拆分器窗格。  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a>更改现有应用程序中的样式  
 如果您要更改现有应用程序中的窗口特性，请改为按照本文的其余部分中的说明。  
  
 若要更改使用的框架应用程序使用应用程序向导创建的默认窗口特性，重写窗口的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)虚拟成员函数。 `PreCreateWindow`允许应用程序访问通常由在内部管理的创建过程[CDocTemplate](../mfc/reference/cdoctemplate-class.md)类。 框架调用`PreCreateWindow`之前创建窗口。 通过修改[CREATESTRUCT](../mfc/reference/createstruct-structure.md)结构传递给`PreCreateWindow`，你的应用程序可以更改用于创建窗口的属性。 例如，若要确保窗口不使用标题，请使用以下的按位运算：  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 [CTRLBARS](../visual-cpp-samples.md)示例应用程序演示这一更改窗口特性用于方法。 具体取决于你的应用程序中的更改`PreCreateWindow`，则可能必须调用该函数的基类实现。  
  
 以下讨论介绍 SDI 用例和[MDI 用例](#_core_the_mdi_case)。  
  
##  <a name="_core_the_sdi_case"></a>SDI 用例  
 在单文档界面 (SDI) 应用程序中，框架的默认窗口样式是的组合**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**样式。 **FWS_ADDTOTITLE**是一种特定于 MFC 的型，它指示要添加到窗口的标题的文档标题的框架。 若要更改窗口特性 SDI 应用程序中的，重写`PreCreateWindow`函数中你的类派生自`CFrameWnd`(其中的应用程序向导名称`CMainFrame`)。 例如:   
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 此代码创建一个主框架窗口最小化和最大化按钮而不相当多的边框。 在屏幕上居中最初显示窗口。  
  
##  <a name="_core_the_mdi_case"></a>MDI 用例  
 稍有更多工作需要更改处于多文档界面 (MDI) 应用程序的子窗口的窗口样式。 默认情况下使用应用程序向导创建的 MDI 应用程序使用默认值[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)在 MFC 中定义的类。 若要更改的 MDI 子窗口的窗口样式，必须派生新类从`CMDIChildWnd`，并将所有引用`CMDIChildWnd`项目中包含对新的类的引用。 最有可能，对的唯一引用`CMDIChildWnd`应用程序中位于应用程序的`InitInstance`成员函数。  
  
 在 MDI 应用程序中使用的默认窗口样式是的组合**WS_CHILD**， **WS_OVERLAPPEDWINDOW**，和**FWS_ADDTOTITLE**样式。 若要更改 MDI 应用程序的子窗口的窗口特性，重写[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)函数中你的类派生自`CMDIChildWnd`。 例如:   
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 此代码将创建 MDI 子窗口，没有最大化按钮。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
-   [窗口样式](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## <a name="see-also"></a>另请参阅  
 [框架窗口样式](../mfc/frame-window-styles-cpp.md)

