---
title: "MDI 选项卡式组 | Microsoft Docs"
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
  - "mdi, 选项卡式组"
  - "选项卡式组"
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# MDI 选项卡式组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多文档界面 \(MDI\) \(MDI\) 制表符分隔的组功能启用多文档界面 \(MDI\) \(MDI\) 应用程序以显示一个或多个选项卡式选项卡式窗口的窗口 \(或组，称为 *制表符分隔的组*\) 的 MDI 工作区。  选项卡式窗口可以垂直滚动还是水平对齐。  如果应用程序承载多个 MDI 制表符分隔的组，这些组由拆分分隔。  
  
## 功能  
 下面是 MDI 制表符分隔的组功能：  
  
-   应用程序可以动态创建选项卡式窗口。  
  
-   应用程序可以水平或垂直对齐选项卡式窗口。  
  
-   选项卡式窗口组的组对象由拆分分隔。  使用拆分，用户可以调整制表符分隔的组。  
  
-   用户可以拖动各个组之间的各选项卡。  
  
-   用户可以拖动各个选项卡创建新组。  
  
-   使用快捷菜单，用户可以移动任何选项卡或创建新组。  
  
-   应用程序可以节省加载和选项卡式窗口布局。  
  
-   应用程序可以节省加载和 MDI 文档的列表。  
  
-   应用程序可以访问各个制表符分隔的组和修改其参数。  
  
### MDI 使用制表符分隔的组  
 以下是任务通常执行与 MDI 制表符分隔的组：  
  
-   实现主框架窗口的 MDI 制表符分隔的组，调用 [CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md)。  此方法的第二个参数是 `CMDITabInfo` 类的实例。  在调用 `CMDIFrameWndEx::EnableMDITabbedGroups`之前，可以使用默认参数或修改它们。  
  
-   修改 MDI 制表符分隔组的属性，在运行时创建或修改 `CMDITabInfo` 对象并再次调用 `CMDIFrameWndEx::EnableMDITabbedGroups`  
  
-   若要获取 MDI 列表选项卡式窗口，名为 `CMDIFrameWndEx::GetMDITabGroups`。  
  
-   单击活动制表符分隔的组旁边以创建新的 MDI 制表符分隔的组，称为 `CMDIFrameWndEx::MDITabNewGroup`。  
  
-   输入点移动为制表符分隔的上一个或下一个窗口，名为 `CMDIFrameWndEx::MDITabMoveToNextGroup`。  
  
-   确定窗口是否为 MDI 制表符分隔的组称为 `CMDIFrameWndEx::IsMemberOfMDITabGroup`的成员。  
  
-   MDI 确定选项卡或 MDI 制表符分隔的组是否用于主框架窗口启用，调用 `CMDIFrameWndEx::AreMDITabs`。  MDI 确定制表符分隔的组是否启用，只调用 `CMDIFrameWndEx::IsMDITabbedGroup`。  
  
-   若要查看快捷菜单，用户在单击选项卡或将该项拖动到另 MDI 制表符分隔的组时，请重写 `CMDIFrameWndEx`的 `CMDIFrameWndEx::OnShowMDITabContextMenu` 派生类。  如果您不执行此方法，应用程序不将显示快捷菜单。  
  
-   保存 MDI 制表符分隔的组布局应用程序，调用 `CMDIFrameWndEx::SaveMDIState`。  若要加载以前保存的 MDI 制表符分隔的组配置文件，请调用 `CMDIFrameWndEx::LoadMDIState`。  在 MDI 应用程序还可以调用这些方法加载或保存已打开文档的列表。  有关保存和加载 MDI 状态的更多信息，请参见 [CMDIFrameWndEx::LoadMDIState](../Topic/CMDIFrameWndEx::LoadMDIState.md)。  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [CMDIFrameWndEx 类](../mfc/reference/cmdiframewndex-class.md)   
 [CMDIChildWndEx 类](../mfc/reference/cmdichildwndex-class.md)   
 [CMDITabInfo Class](../mfc/reference/cmditabinfo-class.md)