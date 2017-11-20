---
title: "工具栏基础知识 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RT_TOOLBAR
dev_langs: C++
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
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55e6df559d6a8365635cea7e94d20bd2576d2273
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="toolbar-fundamentals"></a>工具栏基础知识
本文介绍基本的 MFC 实现，允许你将默认工具栏添加到你的应用程序，通过在应用程序向导中选择一个选项。 涉及主题包括：  
  
-   [应用程序向导工具栏选项](#_core_the_appwizard_toolbar_option)  
  
-   [在代码中的工具栏](#_core_the_toolbar_in_code)  
  
-   [编辑工具栏资源](#_core_editing_the_toolbar_resource)  
  
-   [多个工具栏](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a>应用程序向导工具栏选项  
 若要获取带有默认按钮的单个工具栏，选择标记为用户界面功能页上的标准停靠工具栏选项。 这将代码添加到你的应用程序的：  
  
-   创建工具栏对象。  
  
-   管理工具栏上，包括其具有停靠或浮动的能力。  
  
##  <a name="_core_the_toolbar_in_code"></a>在代码中的工具栏  
 工具栏是[CToolBar](../mfc/reference/ctoolbar-class.md)作为你的应用程序的数据成员声明对象**CMainFrame**类。 换而言之，工具栏对象嵌入主框架窗口对象。 这意味着 MFC 创建工具栏，当它创建框架窗口并销毁工具栏在销毁框架窗口。 下面的分部类声明，对于多文档界面 (MDI) 应用程序，显示了嵌入的工具栏和嵌入式的状态栏的数据成员。 它还显示重写`OnCreate`成员函数。  
  
 [!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]  
  
 工具栏创建出现在**CMainFrame::OnCreate**。 MFC 调用[OnCreate](../mfc/reference/cwnd-class.md#oncreate)后创建窗口的帧但变成可见之前。 默认值`OnCreate`，生成应用程序向导将执行以下工具栏任务：  
  
1.  调用`CToolBar`对象的[创建](../mfc/reference/ctoolbar-class.md#create)成员函数来创建基础[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。  
  
2.  调用[LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)加载工具栏资源信息。  
  
3.  调用函数，可以让停靠、 浮动和工具提示。 有关这些调用详细信息，请参阅文章[停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)。  
  
> [!NOTE]
>  MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)包括旧和新 MFC 工具栏的说明。 使用工具栏**COldToolbar**需要在步骤 2 到中的调用`LoadBitmap`(而非`LoadToolBar`) 并对其`SetButtons`。 新工具栏需要调用`LoadToolBar`。  
  
 停靠、 浮动和工具提示的调用是可选的。 你可以删除这些行从`OnCreate`如果你愿意。 结果是一个工具栏，保持固定，不能浮动或重新停靠和无法显示工具提示。  
  
##  <a name="_core_editing_the_toolbar_resource"></a>编辑工具栏资源  
 默认的工具栏，可以使用应用程序向导基于**RT_TOOLBAR** MFC 4.0 版中引入的自定义资源。 你可以编辑与此资源[工具栏编辑器](../windows/toolbar-editor.md)。 编辑器，可以轻松地添加、 删除和重新排列按钮。 它包含非常类似于 Visual c + + 中的常规图形编辑器的按钮的图形编辑器。 如果你编辑在以前版本的 Visual c + + 工具栏，你将找到任务要容易得多现在。  
  
 若要连接到的命令的工具栏按钮，你为按钮的命令 ID，如`ID_MYCOMMAND`。 在工具栏编辑器中的按钮的属性页中指定的命令 ID。 然后创建该命令的处理程序函数 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)有关详细信息)。  
  
 新[CToolBar](../mfc/reference/ctoolbar-class.md)成员函数使用**RT_TOOLBAR**资源。 [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)现在代替[LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap)加载的工具栏按钮图像、 位图和[SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons)设置按钮样式并连接位图图像按钮。  
  
 有关使用工具栏编辑器的详细信息，请参阅[工具栏编辑器](../windows/toolbar-editor.md)。  
  
##  <a name="_core_multiple_toolbars"></a>多个工具栏  
 应用程序向导为你提供了一个默认的工具栏。 如果你的应用程序中需要多个工具栏，可以基于默认的工具栏向导生成的代码的其他工具栏代码进行建模。  
  
 如果你想要作为命令的结果显示工具栏，你将需要：  
  
-   使用工具栏编辑器创建新的工具栏资源并加载在`OnCreate`与[LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar)成员函数。  
  
-   嵌入新[CToolBar](../mfc/reference/ctoolbar-class.md)在主框架窗口类的对象。  
  
-   请在相应的函数调用`OnCreate`停靠或浮动工具栏、 设置其样式中，依次类推。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [MFC 工具栏实现 （在工具栏上的概述信息）](../mfc/mfc-toolbar-implementation.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具栏工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类  
  
-   [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>另请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)

