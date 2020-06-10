---
title: 界面元素
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 4d4d81287cb30a7d3608025085cdb3f9a208147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619983"
---
# <a name="interface-elements"></a>界面元素

本文档介绍了在 Visual Studio 2008 SP1 中引入的接口元素，还介绍了与库的早期版本之间的差异。

下图显示了使用新的接口元素生成的应用程序。

![MFC 功能包示例应用程序](../mfc/media/mfc_featurepack.png "MFC 功能包示例应用程序")

## <a name="window-docking"></a>窗口停靠

窗口停靠功能类似于 Visual Studio 图形用户界面所使用的窗口停靠。

## <a name="control-bars-are-now-panes"></a>控件条现在是窗格

控件条现在称为窗格，并且派生自[CBasePane 类](reference/cbasepane-class.md)。 在 MFC 的早期版本中，控件条的基类为 `CControlBar` 。

应用程序主框架窗口通常由[CFrameWndEx 类](reference/cframewndex-class.md)或[CMDIFrameWndEx 类](reference/cmdiframewndex-class.md)表示。 主框架称为*停靠站点*。 窗格可以具有三种类型的父项之一：停靠站点、停靠栏或微型框架窗口。

有两种类型的窗格：不可调整大小和可调整大小。 可以使用拆分器或滑块调整可调整大小的窗格，如状态栏和工具栏。 可调整大小的窗格可以构成容器（一个窗格可以停靠到另一个窗格，在其中创建拆分器）。 但是，不能将可调整大小的窗格附加（停靠）到停靠栏。

如果你的应用程序使用不可调整大小的窗格，请从[CPane 类](reference/cpane-class.md)中派生它们。  如果你的应用程序使用可调整大小的窗格，请从[CDockablePane 类](reference/cdockablepane-class.md)中派生它们

## <a name="dock-site"></a>停靠站点

停靠站点（或主框架窗口）拥有应用程序中的所有窗格和袖珍框架窗口。 停靠站点包含[CDockingManager](reference/cdockingmanager-class.md)成员。 此成员维护属于停靠站点的所有窗格的列表。 列表按顺序排列，以便在停靠站点的外边缘创建的窗格位于列表的开头。 当框架重绘停靠站点时，它会遍历此列表，并调整每个窗格的布局，使其包含停靠站点的当前边框。 `AdjustDockingLayout` `RecalcLayout` 当必须调整停靠布局，并且框架将此调用重定向到停靠管理器时，可以调用或。

## <a name="dock-bars"></a>停靠栏

每个主框架窗口都可以沿其边框放置*停靠条*。 停靠栏是属于[CDockSite 类](reference/cdocksite-class.md)的窗格。 停靠栏可以接受从[CPane](reference/cpane-class.md)派生的对象，如工具栏。 若要在初始化主框架窗口时创建停靠条，请调用 `EnableDocking` 。 若要启用自动隐藏栏，请调用 `EnableAutoHideBars` 。 `EnableAutoHideBars`创建[CAutoHideDockSite](reference/cautohidedocksite-class.md)对象，并将它们放置在每个停靠栏的旁边。

每个停靠条分成停靠行。 停靠行由[CDockingPanesRow 类](reference/cdockingpanesrow-class.md)表示。 每个 dock 行都包含一个工具栏列表。 如果用户将工具栏停靠在同一停靠栏中，或将工具栏从一个行移到另一个行，则该框架会创建一个新行并相应地调整停靠栏的大小，或者将该工具栏定位到现有行。

## <a name="mini-frame-windows"></a>袖珍框架窗口

浮动窗格位于袖珍框架窗口中。 袖珍框架窗口由两个类表示： [CMDITabInfo 类](reference/cmditabinfo-class.md)（它只能包含一个窗格）和[CMultiPaneFrameWnd 类](reference/cmultipaneframewnd-class.md)（可包含多个窗格）。 若要在代码中浮动窗格，请调用[CBasePane：： FloatPane](reference/cbasepane-class.md#floatpane)。 在一个窗格浮动后，框架会自动创建一个袖珍框架窗口，并将该袖珍框架窗口变为浮动窗格的父窗口。 当浮动窗格停靠时，框架将重置其父级，并且浮动窗格将成为停靠栏（适用于工具栏）或停靠站点（适用于可调整大小的窗格）。

## <a name="pane-dividers"></a>窗格分隔符

窗格分隔线（也称为滑杆或拆分器）由[CPaneDivider 类](reference/cpanedivider-class.md)表示。 当用户停靠一个窗格时，框架会创建窗格分隔线，而不管该窗格是停靠在停靠站点还是其他窗格上。 当窗格停靠到停靠站点时，窗格分隔符称为*默认窗格分隔线*。 默认窗格分隔符负责停靠站点中所有停靠窗格的布局。 停靠管理器维护默认窗格分隔符列表和窗格列表。 停靠管理器负责所有停靠窗格的布局。

## <a name="containers"></a>容器

所有可以调整大小的窗格在容器中进行维护。 容器由[CPaneContainer 类](reference/cpanecontainer-class.md)表示。 每个容器都有指向其左窗格、右窗格、左侧子容器、右子容器和左和右部分之间拆分器的指针。 （*左*和*右*不是指物理边，而是确定树结构的分支。）通过这种方式，我们可以生成窗格和拆分器的树，从而实现可以调整大小的窗格的复杂布局。 `CPaneContainer`类维护容器树; 它还维护位于此树中的两个窗格和滑块列表。 窗格容器管理器通常嵌入到具有多个窗格的默认滑块和袖珍框架窗口中。

## <a name="auto-hide-control-bars"></a>自动隐藏控制条

默认情况下，每个都 `CDockablePane` 支持自动隐藏功能。 当用户单击标题上的 "固定" 按钮时 `CDockablePane` ，框架会将窗格切换为自动隐藏模式。 为了处理单击，框架创建了一个[CMFCAutoHideBar 类](reference/cmfcautohidebar-class.md)和一个与该对象关联的[CMFCAutoHideButton 类](reference/cmfcautohidebutton-class.md) `CMFCAutoHideBar` 。 框架将新的放 `CMFCAutoHideBar` 在[CAutoHideDockSite](reference/cautohidedocksite-class.md)上。 框架还将附加 `CMFCAutoHideButton` 到工具栏。 [CDockingManager 类](reference/cdockingmanager-class.md)维护 `CDockablePane` 。

## <a name="tabbed-control-bars-and-outlook-bars"></a>选项卡式控件条和 Outlook 栏

[CMFCBaseTabCtrl 类](reference/cmfcbasetabctrl-class.md)使用可分离选项卡实现选项卡式窗口的基本功能。 若要使用 `CMFCBaseTabCtrl` 对象，请在应用程序中初始化[CBaseTabbedPane 类](reference/cbasetabbedpane-class.md)。 `CBaseTabbedPane`派生自 `CDockablePane` 并维护指向对象的指针 `CMFCBaseTabCtrl` 。 `CBaseTabbedPane`允许用户停靠选项卡式控制条并调整其大小。 使用[CDockablePane：： AttachToTabWnd](reference/cdockablepane-class.md#attachtotabwnd)动态创建停靠和选项卡式的控制条。

Outlook bar 控件也基于选项卡式栏。 [CMFCOutlookBar 类](reference/cmfcoutlookbar-class.md)派生自 `CBaseTabbedPane` 。 有关如何使用 Outlook 面板的详细信息，请参阅[CMFCOutlookBar 类](reference/cmfcoutlookbar-class.md)。

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)
