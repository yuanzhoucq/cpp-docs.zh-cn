---
title: "界面元素 | Microsoft Docs"
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
  - "体系结构 [C++], MFC 功能包"
  - "MFC 功能包, 体系结构"
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# 界面元素
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档介绍 [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] SP1 中引入的接口元素，它描述与库的早期版本的区别。  
  
 下图显示了使用的新接口元素，生成的应用程序。  
  
 ![MFC 功能包示例应用程序](../mfc/media/mfc_featurepack.png "MFC\_FeaturePack")  
  
## 窗口停靠  
 窗口停靠功能与 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 图形用户界面使用的窗口停靠。  
  
## 控件条现在是窗格  
 控件条现在称为窗格并从派生。[CBasePane Class](../mfc/reference/cbasepane-class.md) 在 MFC 中，早期版本控件条基类是 `CControlBar`。  
  
 应用程序主框架窗口由 [CFrameWndEx Class](../mfc/reference/cframewndex-class.md) 或 [CMDIFrameWndEx 类](../mfc/reference/cmdiframewndex-class.md)通常表示。  主框架调用 *停靠站点*。  窗格可以具有父级的三种类型之一：停靠站点、停靠或栏微型框窗口。  
  
 窗格中有两种类型：不可重新调整和可调整大小。  使用拆分或滑块，可调整大小中，如状态栏和工具栏\)，它可以调整大小。  可重新调整的窗格中窗体容器 \(一窗格可以停靠到其他窗格，创建在它们之间进行拆分。\)  但是，可调整大小的栏停靠窗格不能附加 \(停靠\)。  
  
 如果应用程序使用不可重新调整的窗格，请从 [CPane Class](../mfc/reference/cpane-class.md)派生它们。如果应用程序使用可重新调整的窗格，请从 [CDockablePane Class](../mfc/reference/cdockablepane-class.md)派生它们  
  
## 停靠站点  
 停靠站点 \(或主框架窗口\) 拥有所有窗格和要框"应用程序。  停靠站点包含一个成员。[CDockingManager](../mfc/reference/cdockingmanager-class.md) 此成员保留属于固定站点所有窗格的列表。  列表排序，以便创建在站点的停靠窗格外边缘在列表的开始位置。  当框架重新停靠站点内循环时，该列表对包含停靠网站的当前范围矩形调整每个窗格布局。  您可以调用 `AdjustDockingLayout` 或 `RecalcLayout`，则您必须调整停靠布局时，而框架重定向此调用向停靠管理器。  
  
## 条停靠  
 每个主框架窗口可以沿其边界的 *Dock 条*。  停靠栏是属于 [CDockSite Class](../mfc/reference/cdocksite-class.md)的窗格。  停靠条可以接受从 [CPane](../mfc/reference/cpane-class.md)派生的对象，如工具栏。  若要创建一条停靠，在主框架窗口初始化时，请调用 `EnableDocking`。  若要启用自动隐藏条，请调用 `EnableAutoHideBars`。  `EnableAutoHideBars` 创建对象，并在 [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) 每个停靠条旁边确定它们。  
  
 每个停靠栏分为停靠行。  停靠行已被 [CDockingPanesRow Class](../mfc/reference/cdockingpanesrow-class.md)表示。  每个行包含停靠工具栏列表。  如果用户停靠工具栏移动或从一行的工具栏为另一种。同一个停靠栏中，框架或创建新行并相应地调整停靠条，或者在现有行确定工具栏。  
  
## 微型框窗口  
 浮动窗格位于微型框窗口。  微型框窗口。表示两类：只能包含一窗格\) 可以包含多窗格\) 中的 [CMDITabInfo Class](../mfc/reference/cmditabinfo-class.md) \(\) 和 [CMultiPaneFrameWnd Class](../mfc/reference/cmultipaneframewnd-class.md) \(。  浮动代码中的一个窗格，调用 [CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md)。  在浮动窗格之后，框架会自动创建要框窗口中，该窗口浮动窗格微型框变为的父级。  在浮动窗格停靠时，框架将重置其父，并且，浮动窗格变成条停靠工具栏 \(对于\) 或停靠站点 \(为大小可调的窗格。\)  
  
## 窗格分隔符  
 分隔符窗格 \(也称为滑块或拆分器\)。[CPaneDivider Class](../mfc/reference/cpanedivider-class.md)表示。  当用户窗格停靠时，框架创建窗格分隔符，而不管窗格是停靠在停靠站点或在另一个窗格。  如果窗格停靠到停靠窗格的调用站点时，*默认窗格*分隔线。  默认窗格分隔对所有停靠在停靠窗格布局运行站点。  停靠管理器保持默认窗格的列表和窗格的列表。  停靠管理器运行所有停靠窗格布局。  
  
## 容器  
 所有可调整大小中，当容器中停靠，彼此进行维护。  容器通过 [CPaneContainer Class](../mfc/reference/cpanecontainer-class.md)表示。  每个容器包含指向其左窗格、右、子窗格左侧容器、正确的子容器和拆分。和部件之间。\(*和* 不引用实际端，而标识树结构所始于的分支。\)这样就可以生成和拆分窗格树并实现可以一起调整窗格的复杂的布局。  `CPaneContainer` 类维护容器树；位于此树中还维护窗格两个列表和滑块。  容器通常窗格管理器嵌入具有多个窗格的默认和滑块微型框窗口。  
  
## 自动隐藏控件条  
 默认情况下，每个 `CDockablePane` 都支持自动隐藏功能。  当用户单击 `CDockablePane`控件上的标题时固定按钮切换窗格，框架自动隐藏模式。  若要处理单击框架创建，并与 [CMFCAutoHideBar Class](../mfc/reference/cmfcautohidebar-class.md)[CMFCAutoHideButton Class](../mfc/reference/cmfcautohidebutton-class.md)`CMFCAutoHideBar` 对象。  框架上 [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)将新的 `CMFCAutoHideBar`。  框架还将 `CMFCAutoHideButton` 附加到工具栏。  [CDockingManager Class](../mfc/reference/cdockingmanager-class.md) 维护 `CDockablePane`。  
  
## 选项卡式控件条和 Outlook 栏  
 [CMFCBaseTabCtrl Class](../mfc/reference/cmfcbasetabctrl-class.md) 一个选项卡式窗口的基本功能。可拆的选项卡中。  为了使用 `CMFCBaseTabCtrl` 对象，初始化在的应用程序 [CBaseTabbedPane 类](../mfc/reference/cbasetabbedpane-class.md)。  `CBaseTabbedPane` 从 `CDockablePane` 派生并维护指向 `CMFCBaseTabCtrl` 对象的指针。  `CBaseTabbedPane` 允许用户调整停靠和选项卡式控件条。  使用 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) 动态创建停靠和选项卡式控件条。  
  
 Outlook 栏控件基于选项卡式栏也。  [CMFCOutlookBar 类](../mfc/reference/cmfcoutlookbar-class.md) 从 `CBaseTabbedPane`派生。  有关如何使用 Outlook 栏的更多信息，请参见 [CMFCOutlookBar 类](../mfc/reference/cmfcoutlookbar-class.md)。  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)