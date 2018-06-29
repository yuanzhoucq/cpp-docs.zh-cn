---
title: 界面元素 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1906505e75273cc62a0eac55e6ed1a9686a3b76f
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078439"
---
# <a name="interface-elements"></a>界面元素
本文档介绍在 Visual Studio 2008 SP1 中，引入的界面元素，并还介绍了与该早期版本的库的差异。  
  
 下图显示了通过使用新的界面元素生成的应用程序。  
  
 ![MFC 功能包示例应用程序](../mfc/media/mfc_featurepack.png "mfc_featurepack")  
  
## <a name="window-docking"></a>停靠窗口  
 窗口停靠功能类似于窗口停靠，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]图形用户界面使用。  
  
## <a name="control-bars-are-now-panes"></a>控件条是现在窗格  
 控件条现在称为窗格和派生自[CBasePane 类](../mfc/reference/cbasepane-class.md)。 在早期版本的 MFC，控件条的基类是`CControlBar`。  
  
 应用程序主框架窗口通常由[CFrameWndEx 类](../mfc/reference/cframewndex-class.md)或[CMDIFrameWndEx 类](../mfc/reference/cmdiframewndex-class.md)。 主框架称为*停靠站点*。 窗格可以具有的父级的三种类型之一： 停靠站点、 停靠栏中或微型框架窗口。  
  
 有两种类型的窗格： 无法调整大小和可调整大小。 可调整大小的窗格，如状态栏和工具栏，可以通过使用拆分条中或滑块调整大小。 可调整大小的窗格可以形成 （一个窗格可以停靠到另一个窗格中，创建它们之间拆分） 的容器。 但是，不能 （停靠） 停靠条附加可调整大小的窗格。  
  
 如果你的应用程序使用非可调整大小的窗格，派生从[CPane 类](../mfc/reference/cpane-class.md)。  如果你的应用程序使用可调整大小的窗格，派生从[CDockablePane 类](../mfc/reference/cdockablepane-class.md)  
  
## <a name="dock-site"></a>停靠站点  
 停靠站点 （或主框架窗口） 拥有所有窗格和在应用程序的微型框架窗口。 停靠站点包含[CDockingManager](../mfc/reference/cdockingmanager-class.md)成员。 此成员维护属于停靠站点的所有窗格的列表。 列表进行排序，以便创建在停靠站点的外边缘的窗格位于列表的开头。 当框架重绘停靠站点时，它将循环访问此列表并调整每个窗格，以包括停靠站点的当前边框的布局。 你可以调用`AdjustDockingLayout`或`RecalcLayout`当你具有以调整停靠布局，并且该框架将重定向到停靠管理器对的调用。  
  
## <a name="dock-bars"></a>停靠栏  
 每个主框架窗口可以放置*停靠条*沿其边框。 停靠栏是属于一个窗格[CDockSite 类](../mfc/reference/cdocksite-class.md)。 停靠栏可以接受派生自[CPane](../mfc/reference/cpane-class.md)，如工具栏。 若要创建停靠栏，在初始化主框架窗口时，调用`EnableDocking`。 若要启用自动隐藏栏，请调用`EnableAutoHideBars`。 `EnableAutoHideBars` 创建[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)对象，并将它们置于每个停靠栏旁边。  
  
 每个停靠栏划分为停靠行。 由表示停靠行[CDockingPanesRow 类](../mfc/reference/cdockingpanesrow-class.md)。 每个停靠行包含工具栏的列表。 如果用户将工具栏停靠，或某一行中的工具栏移动到另一种相同的停靠栏，框架创建一个新行，并相应地，调整停靠栏的大小或它位置工具栏上的现有行。  
  
## <a name="mini-frame-windows"></a>微型框架窗口  
 浮动窗格驻留在微型框架窗口。 由两个类表示微型框架窗口： [CMDITabInfo 类](../mfc/reference/cmditabinfo-class.md)（可以包含一个窗格中） 和[CMultiPaneFrameWnd 类](../mfc/reference/cmultipaneframewnd-class.md)（可以包含多个窗格）。 若要在代码中浮动窗格，调用[CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane)。 浮动窗格中之后，框架会自动创建微型框架窗口，并且该微型框架窗口将成为浮动窗格的父级。 时浮动窗格停靠，框架将重置其父级，且浮动窗格成为停靠栏 （对于工具栏） 或停靠站点 （适用于可调整大小的窗格）。  
  
## <a name="pane-dividers"></a>窗格中的分隔线  
 （也称为滑块或拆分条中） 的窗格中分隔条由[CPaneDivider 类](../mfc/reference/cpanedivider-class.md)。 当用户停靠窗格中时，框架将创建窗格中的分隔线，无论是否窗格停靠在停靠站点上或在另一个窗格中。 当到停靠站点停靠窗格中时，被调用的窗格分隔条*默认窗格分隔线*。 默认窗格分隔条负责在停靠站点中所有停靠的窗格的布局。 停靠管理器维护的默认窗格中的分隔线，列表和窗格的列表。 停靠管理器负责所有停靠的窗格的布局。  
  
## <a name="containers"></a>容器  
 在容器中维护所有可调整大小的窗格，停靠到对方时。 由表示容器[CPaneContainer 类](../mfc/reference/cpanecontainer-class.md)。 每个容器都有指向其左窗格中、 右窗格中、 左子容器、 右子容器和拆分器左侧和右侧的各个部件之间。 (*左*和*右*物理边不引用的但而是确定树状结构的分支。)以这种方式中，我们可以生成的窗格和拆分条节点树，并因此实现可以一起调整大小的窗格的复杂布局。 `CPaneContainer`类保留容器的树; 它还保留两个列表的窗格和驻留在此树中的滑块。 窗格容器管理器通常会嵌入到默认滑块和执行多个窗格的微型框架窗口中。  
  
## <a name="auto-hide-control-bars"></a>自动隐藏控件条  
 默认情况下，每个`CDockablePane`支持自动隐藏功能。 当用户单击的标题上的 pin 按钮`CDockablePane`，框架切换到自动隐藏模式的窗格。 若要处理单击，框架会创建[CMFCAutoHideBar 类](../mfc/reference/cmfcautohidebar-class.md)和[CMFCAutoHideButton 类](../mfc/reference/cmfcautohidebutton-class.md)与关联`CMFCAutoHideBar`对象。 框架放入新`CMFCAutoHideBar`上[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)。 框架还会将附加`CMFCAutoHideButton`到工具栏。 [CDockingManager 类](../mfc/reference/cdockingmanager-class.md)维护`CDockablePane`。  
  
## <a name="tabbed-control-bars-and-outlook-bars"></a>选项卡式的控件条和 Outlook 栏  
 [CMFCBaseTabCtrl 类](../mfc/reference/cmfcbasetabctrl-class.md)实现可拆分的选项卡的选项卡式窗口的基本功能。 若要使用`CMFCBaseTabCtrl`对象，初始化[CBaseTabbedPane 类](../mfc/reference/cbasetabbedpane-class.md)应用程序中。 `CBaseTabbedPane` 派生自`CDockablePane`和维护着一个指针到`CMFCBaseTabCtrl`对象。 `CBaseTabbedPane`使用户能够停靠和调整大小选项卡式的控件条。 使用[cdockablepane:: Attachtotabwnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd)动态创建的停靠和选项卡式控件条。  
  
 Outlook 栏控件还基于选项卡式条。 [CMFCOutlookBar 类](../mfc/reference/cmfcoutlookbar-class.md)派生自`CBaseTabbedPane`。 有关如何使用 Outlook 栏的详细信息，请参阅[CMFCOutlookBar 类](../mfc/reference/cmfcoutlookbar-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [概念](../mfc/mfc-concepts.md)

