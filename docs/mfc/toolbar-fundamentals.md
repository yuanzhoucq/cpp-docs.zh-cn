---
title: "工具栏基础知识 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RT_TOOLBAR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序向导 [C++], 安装默认的应用程序工具栏"
  - "命令 ID, 工具栏按钮"
  - "CToolBar 类, 应用程序向导中的默认工具栏"
  - "在窗口框架类中嵌入工具栏"
  - "框架窗口类, 嵌入的工具栏"
  - "LoadBitmap 方法, 工具栏"
  - "LoadToolBar 方法"
  - "资源 [MFC], 工具栏"
  - "RT_TOOLBAR 资源"
  - "SetButtons 方法"
  - "工具栏控件 [MFC], 命令 ID"
  - "工具栏控件 [MFC], 使用应用程序向导创建的工具栏"
  - "工具栏编辑器, 应用程序向导"
  - "工具栏 [C++], 使用应用程序向导添加默认值"
  - "工具栏 [C++], 创建"
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 工具栏基础知识
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述可以添加工具栏到默认应用程序通过在应用程序向导的选项的基本 MFC 实现。  所涵盖的主题包括：  
  
-   [工具栏应用程序向导选项](#_core_the_appwizard_toolbar_option)  
  
-   [工具栏代码](#_core_the_toolbar_in_code)  
  
-   [工具栏编辑资源](#_core_editing_the_toolbar_resource)  
  
-   [多个工具栏](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a> 工具栏应用程序向导选项  
 若要获取默认按钮的工具栏，一个具有选择标记上用户界面功能的标准页面的停靠工具栏选项。  此代码添加到应用程序中：。  
  
-   创建工具栏对象。  
  
-   管理工具栏，包括它能够停靠或浮动。  
  
##  <a name="_core_the_toolbar_in_code"></a> 工具栏代码  
 工具栏为应用程序的 **CMainFrame** 类的数据成员声明的对象。[CToolBar](../mfc/reference/ctoolbar-class.md) 换言之，工具栏对象在主框架窗口对象嵌入。  这意味着 MFC 创建工具栏，则创建框架窗口时并销毁工具栏，则销毁框架窗口时。  下面的分部类声明，多文档界面 \(MDI\) \(MDI\) 应用程序，显示嵌入式工具栏和嵌入式状态栏的数据成员。  它还演示 `OnCreate` 成员函数的重写。  
  
 [!CODE [NVC_MFCListView#6](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCListView#6)]  
  
 工具栏会在发生 **CMainFrame::OnCreate**。  在创建 MFC 框架的窗口后调用 [OnCreate](../Topic/CWnd::OnCreate.md)，但是，在其变为可见。  应用程序向导生成的 `OnCreate` 默认工具栏执行以下任务：  
  
1.  调用 `CToolBar` 对象的函数 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)[创建](../Topic/CToolBar::Create.md) 成员创建基础对象。  
  
2.  调用 [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) 工具栏资源加载信息。  
  
3.  调用函数启用停靠，浮动和工具提示。  有关这些调用的详细信息，请参见 [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)文章。  
  
> [!NOTE]
>  MFC 泛型示例 [DOCKTOOL](../top/visual-cpp-samples.md) 包含旧的和新 MFC 工具栏的图。  使用 **COldToolbar** 的工具栏需要在步骤 2 的调用为 `LoadBitmap` \(而不是 `LoadToolBar`\) 和 `SetButtons`。  新工具栏需要调用 `LoadToolBar`。  
  
 停靠，浮动工具和提示调用是可选的。  如果您愿意，也可以从 `OnCreate` 移除这些行。  结果是将保持固定或浮动，不 redock 和无法显示工具提示的工具栏。  
  
##  <a name="_core_editing_the_toolbar_resource"></a> 工具栏编辑资源  
 获得与应用程序向导的默认工具栏根据 **RT\_TOOLBAR** 自定义资源，会在 MFC 4.0 版。  可以编辑与 [工具栏编辑器](../mfc/toolbar-editor.md)上为此资源。  编辑器允许您轻松，添加、删除和重新排列按钮。  它包含非常类似于 Visual C\+\+ 的泛图形编辑按钮的图形编辑器。  如果编辑在 Visual C\+\+ 早期版本中的工具栏，您将找到更简单的任务。  
  
 若要连接工具栏按钮。命令，您赋予按钮的命令 ID，如 `ID_MYCOMMAND`。  指定命令 ID 在编辑器工具栏按钮的属性页。  然后创建命令的处理程序函数 \(请参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)。更多信息。\)  
  
 新的 [CToolBar](../mfc/reference/ctoolbar-class.md) 成员函数使用 **RT\_TOOLBAR** 资源一起使用。  [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) 现在取代 [LoadBitmap](../Topic/CToolBar::LoadBitmap.md) 加载工具栏按钮的位图图像和 [SetButtons](../Topic/CToolBar::SetButtons.md) 设置按钮的样式和连接使用位图图像的按钮。  
  
 有关使用工具栏编辑器的详细信息，请参见 [工具栏编辑器](../mfc/toolbar-editor.md)。  
  
##  <a name="_core_multiple_toolbars"></a> 多个工具栏  
 应用程序向导提供一个默认。工具栏  如果在应用程序需要多个工具栏，可以基于默认工具栏模型的向导生成的代码中的工具栏的代码。  
  
 作为命令，则若要显示工具栏，您需要：  
  
-   创建工具栏编辑器的新工具栏资源加载并在 `OnCreate` 为 [LoadToolbar](../Topic/CToolBar::LoadToolBar.md) 成员函数。  
  
-   嵌入在主框架窗口类的新对象。[CToolBar](../mfc/reference/ctoolbar-class.md)  
  
-   调用在相应的 `OnCreate` 函数调用停靠或浮动工具栏，设置其样式，依此类推。  
  
### 您想进一步了解什么？  
  
-   [MFC 工具栏实现 \(在工具栏的概述信息\)](../mfc/mfc-toolbar-implementation.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具栏的工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 类  
  
-   [与工具栏控件。](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用以前的工具栏](../mfc/using-your-old-toolbars.md)  
  
## 请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)