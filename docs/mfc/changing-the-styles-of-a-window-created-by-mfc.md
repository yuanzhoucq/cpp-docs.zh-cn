---
title: "更改 MFC 创建的窗口的样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWnd 类, 窗口样式"
  - "子窗口, 样式"
  - "CMainFrame 类"
  - "CMDIChildWnd 类, 更改窗口样式"
  - "CREATESTRUCT 宏"
  - "默认窗口样式"
  - "默认值 [C++], 窗口样式"
  - "MDI [C++], 窗口样式"
  - "MFC [C++], 窗口"
  - "多文档界面样式"
  - "PreCreateWindow 方法, 更改窗口样式"
  - "PreCreateWindow 方法, 窗口样式"
  - "单文档界面 (SDI), 更改窗口特性"
  - "单文档界面 (SDI), 样式"
  - "样式, 窗口"
  - "窗口样式 [C++]"
  - "窗口 [C++], MFC"
  - "WS_OVERLAPPEDWINDOW 宏"
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 更改 MFC 创建的窗口的样式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在其的 `WinMain` 函数的版本，MFC 将注册您的若干标准窗口类。  由于通常不编辑 MFC 的 `WinMain`，则该函数不使您有机会更改 MFC 默认窗口样式。  本文说明如何能够更改这样的预注册窗口类样式在现有的应用程序中。  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> 将新的样式的 MFC 应用程序  
 如果您使用 Visual C\+\+ 2.0 或更高版本，则您可更改应用程序向导的默认窗口样式，当您创建应用程序时。  在应用程序向导的用户界面功能，页面可以更改主框架窗口和 MDI 子窗口的样式。  对于任一窗口类型，可以指定其帧粗细 \(粗细或\) 和任何以下操作：  
  
-   最大化或最小化窗口是否有控件。  
  
-   最初，最大化或最小化窗口是否显示二者都不是。  
  
 对于主框架窗口，还可以指定窗口是否有系统菜单。  在 MDI 子窗口，可以指定是否支持拆分窗口窗格。  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a> 将一个现有应用程序的样式  
 如果将现有的应用程序窗口的特性，请按照其余的指令本文。  
  
 若要更改框架应用程序使用特性的默认窗口创建与应用程序向导，请重写窗口中 [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) 虚成员函数。  `PreCreateWindow` 允许应用程序访问 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) 类内部通常管理的创建过程。  框架在创建窗口之前调用 `PreCreateWindow`。  通过修改 [CREATESTRUCT](../mfc/reference/createstruct-structure.md) 结构传递给 `PreCreateWindow`，应用程序可以更改用于创建窗口的特性。  例如，确保窗口未使用标题，请使用下列位操作：  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 [CTRLBARS](../top/visual-cpp-samples.md) 示例应用程序演示更改窗口特征的此方法。  根据应用程序在 `PreCreateWindow`更改，请调用函数的基类实现可能是必需的。  
  
 以下讨论 SDI 包括用例和 [MDI 情况](#_core_the_mdi_case)。  
  
##  <a name="_core_the_sdi_case"></a> SDI 用例  
 在单文档界面 \(SDI\) \(SDI\) 应用程序，框架中的默认窗口样式是 **WS\_OVERLAPPEDWINDOW** 和 **FWS\_ADDTOTITLE** 样式的组合。  **FWS\_ADDTOTITLE** 是一框架添加标题。文档窗口的标题、用 MFC 特定样式。  若要更改在 SDI 应用程序窗口的特性，重写从应用程序向导名为 `CMainFrame`\) 的 `CFrameWnd` 派生类的 `PreCreateWindow` 函数 \(。  例如：  
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 此代码创建非主框架窗口最小化和最大化按钮，然后不带调整边框。  窗口在屏幕最初居中。  
  
##  <a name="_core_the_mdi_case"></a> MDI 用例  
 有需要执行更多工作。更改一个子窗口的窗口样式在多文档界面 \(MDI\) \(MDI\) 应用程序中。  默认情况下，用创建 MDI 应用程序使用 MFC 应用程序向导。定义的默认类。[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 若要更改 MDI 子窗口的窗口样式，必须从 `CMDIChildWnd` 派生一个新类并将对新类的引用替换对 `CMDIChildWnd` 的所有引用。项目。  可能，对 `CMDIChildWnd` 的引用。应用程序位于应用程序的 `InitInstance` 成员函数。  
  
 在 MDI 应用程序的 Windows 默认样式是 **WS\_CHILD**、**WS\_OVERLAPPEDWINDOW**和 **FWS\_ADDTOTITLE**。样式的组合。  若要更改 MDI 应用程序的子窗口的窗口特性，重写从 `CMDIChildWnd`派生的类的函数。[PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) 例如：  
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 此代码创建 MDI 子窗口，从而无需最大化按钮。  
  
### 您想进一步了解什么？  
  
-   [窗口样式](../mfc/reference/window-styles.md)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
-   [\<caps:sentence id\="tgt44" sentenceid\="26254917059da4aba50f886a6c5db931" class\="tgtSentence"\>窗口样式\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## 请参阅  
 [框架窗口样式](../mfc/frame-window-styles-cpp.md)