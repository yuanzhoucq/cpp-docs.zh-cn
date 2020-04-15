---
title: CDockingManager 类
ms.date: 11/04/2016
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
ms.openlocfilehash: 339e5d5e464aacb51d1c4ab8fe3c2957a3afbd4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375587"
---
# <a name="cdockingmanager-class"></a>CDockingManager 类

实现用于控制主框架窗口中停靠布局的核心功能。

## <a name="syntax"></a>语法

```
class CDockingManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDocking管理器：：添加Dock网站](#adddocksite)|创建停靠窗格并将其添加到控制栏列表中。|
|[CDocking管理器：：添加隐藏MDITabbedbar](#addhiddenmditabbedbar)|将句柄添加到栏窗格到隐藏的 MDI 选项卡栏窗格列表中。|
|[CDocking管理器：：添加Mini框架](#addminiframe)|将框架添加到迷你框架列表中。|
|[CDocking管理器：：添加窗格](#addpane)|向停靠管理器注册窗格。|
|[CDocking管理器：：调整停靠布局](#adjustdockinglayout)|重新计算和调整框架窗口中所有窗格的布局。|
|[CDocking 管理器：：调整窗格框架](#adjustpaneframes)|使WM_NCCALCSIZE消息发送到所有窗格和`CPaneFrameWnd`窗口。|
|[Cdocking管理器：调整到客户端区域](#adjustrecttoclientarea)|调整矩形的对齐方式。|
|[CDocking管理器：对齐自动隐藏窗格](#alignautohidepane)|在自动隐藏模式下调整停靠窗格的大小，以便它占用帧的工作区的全宽或高度，并包围停靠站点。|
|[CDocking管理器：自动隐藏窗格](#autohidepane)|创建自动隐藏工具栏。|
|[CDocking管理器：：带巴斯托托](#bringbarstotop)|将具有指定对齐的停靠条带到顶部。|
|[CDocking管理器：：构建窗格菜单](#buildpanesmenu)|将停靠窗格和工具栏的名称添加到菜单中。|
|[CDocking 管理器：：Calc预期多克已重新](#calcexpecteddockedrect)|计算停靠窗口的预期矩形。|
|[CDocking管理器：创建](#create)|创建停靠管理器。|
|[CDocking管理器：:D](#determinepaneandstatus)|确定包含给定点的窗格及其停靠状态。|
|[CDocking管理器：:D可还原DockDockState](#disablerestoredockstate)|启用或禁用从注册表加载停靠布局。|
|[CDocking管理器：:DockPane](#dockpane)|将窗格停靠到另一个窗格或框架窗口。|
|[对接管理器：:D奥克帕内左](#dockpaneleftof)|将窗格停靠到另一个窗格的左侧。|
|[CDocking 管理器：启用自动隐藏窗格](#enableautohidepanes)|启用窗格与主框架的停靠，创建停靠窗格，并将其添加到控制栏列表中。|
|[CDocking管理器：启用对接](#enabledocking)|创建停靠窗格，并使窗格与主框架对接。|
|[CDocking管理器：启用DockSite菜单](#enabledocksitemenu)|显示一个附加按钮，该按钮在所有停靠窗格的标题上打开一个弹出式菜单。|
|[CDocking管理器：：启用窗格上下文菜单](#enablepanecontextmenu)|告诉库显示一个特殊的上下文菜单，该菜单具有应用程序工具栏和停靠窗格的列表，当用户单击鼠标右键并且库正在处理WM_CONTEXTMENU消息时。|
|[CDocking管理器：：查找DockSite](#finddocksite)|检索位于指定位置且具有指定对齐方式的条形窗格。|
|[CDocking管理器：：查找DocksitebyPane](#finddocksitebypane)|返回具有目标栏窗格 ID 的条形窗格。|
|[CDocking管理器：：查找PaneByID](#findpanebyid)|按指定的控件 ID 查找窗格。|
|[CDocking管理器：修复虚拟重新](#fixupvirtualrects)|将所有当前工具栏位置提交到虚拟矩形。|
|[CDocking管理器：：从点帧](#framefrompoint)|返回包含给定点的帧。|
|[CDocking 管理器：获取客户区域绑定](#getclientareabounds)|获取包含工作区边界的矩形。|
|[CDocking管理器：获取对接模式](#getdockingmode)|返回当前停靠模式。|
|[CDocking管理器：：获取DockSiteFramewnd](#getdocksiteframewnd)|获取指向父窗口框架的指针。|
|[Cdocking 管理器：实现启用自动隐藏对齐](#getenabledautohidealignment)|返回窗格的启用对齐方式。|
|[CDocking管理器：获取迷你框架](#getminiframes)|获取微型帧列表。|
|[CDocking管理器：获取外部边缘绑定](#getouteredgebounds)|获取包含框架外边缘的矩形。|
|[CDocking管理器：获取窗格列表](#getpanelist)|返回属于停靠管理器的窗格列表。 这包括所有浮动窗格。|
|[CDocking管理器：获取智能扩展管理器](#getsmartdockingmanager)|检索指向智能停靠管理器的指针。|
|[CDocking管理器：获取智能扩展管理器永久](#getsmartdockingmanagerpermanent)|检索指向智能停靠管理器的指针。|
|[CDocking管理器：获取智能对接参数](#getsmartdockingparams)|返回停靠管理器的智能停靠参数。|
|[CDocking管理器：获取智能对接主题](#getsmartdockingtheme)|返回用于显示智能停靠标记的主题的静态方法。|
|[CDocking管理器：隐藏自动隐藏窗格](#hideautohidepanes)|隐藏处于自动隐藏模式的窗格。|
|[CDocking管理器：：插入DockSite](#insertdocksite)|创建停靠窗格并将其插入控制栏列表。|
|[CDocking管理器：插入窗格](#insertpane)|将控制窗格插入控制栏列表中。|
|[CDocking管理器：：IsDockSiteMenu](#isdocksitemenu)|指定弹出菜单是否显示在所有窗格的标题上。|
|[Cdocking 管理器：正在调整布局](#isinadjustlayout)|确定是否调整了所有窗格的布局。|
|[CDocking管理器：isOLE容器模式](#isolecontainermode)|指定停靠管理器是否处于 OLE 容器模式。|
|[CDocking管理器：：IsPointNearDockSite](#ispointneardocksite)|确定指定点是否靠近停靠站点。|
|[CDocking管理器：：正在打印预览有效](#isprintpreviewvalid)|确定是否设置了打印预览模式。|
|[CDocking管理器：加载状态](#loadstate)|从注册表加载停靠管理器的状态。|
|[CDocking管理器：锁更新](#lockupdate)|锁定给定的窗口。|
|[CDocking管理器：在激活帧上](#onactivateframe)|当框架窗口变为活动或停用时，由框架调用。|
|[CDocking管理器：：上接合弹出菜单](#onclosepopupmenu)|当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。|
|[Cdocking管理器：在移动迷你框架](#onmoveminiframe)|由框架调用以移动微型框架窗口。|
|[Cdocking管理器：：在窗格上下文菜单](#onpanecontextmenu)|当框架生成包含窗格列表的菜单时，由框架调用。|
|[CDocking管理器：:P从点](#panefrompoint)|返回包含给定点的窗格。|
|[CDocking管理器：:ProcessPane上下文菜单命令](#processpanecontextmenucommand)|由框架调用以选择或清除指定命令的复选框，并重新计算显示的窗格的布局。|
|[CDocking管理器：Recalclayout](#recalclayout)|重新计算控件列表中存在的控件的内部布局。|
|[CDocking 管理器：：释放空窗格容器](#releaseemptypanecontainers)|释放空窗格容器。|
|[CDocking 管理器：：删除隐藏 MDITabbedbar](#removehiddenmditabbedbar)|删除指定的隐藏栏窗格。|
|[CDocking管理器：删除Mini框架](#removeminiframe)|从迷你框架列表中删除指定的帧。|
|[CDockManager：从Dock管理器中删除窗格](#removepanefromdockmanager)|取消注册窗格并将其从停靠管理器中的列表中删除。|
|[CDocking管理器：替换窗格](#replacepane)|用一个窗格替换另一个窗格。|
|[CDocking管理器：：度假村迷你框架为ZOrder](#resortminiframesforzorder)|在迷你帧列表中对帧进行设置。|
|[CDocking管理器：：保存状态](#savestate)|将停靠管理器的状态保存到注册表。|
|[CDocking管理器：：发送消息到微型帧](#sendmessagetominiframes)|将指定的消息发送到所有微型帧。|
|[CDocking管理器：序列化](#serialize)|将停靠管理器写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|
|[CDocking 管理器：设置自动隐藏顺序](#setautohidezorder)|设置控制栏和指定窗格的大小、宽度和高度。|
|[CDocking管理器：设置对接模式](#setdockingmode)|设置停靠模式。|
|[CDocking管理器：：SetDockState](#setdockstate)|设置控制栏、微型框架和自动隐藏栏的停靠状态。|
|[CDocking管理器：：设置打印预览模式](#setprintpreviewmode)|设置打印预览中显示的条形图的打印预览模式。|
|[CDocking管理器：设置智能对接参数](#setsmartdockingparams)|设置定义智能停靠行为的参数。|
|[CDocking管理器：：显示延迟显示迷你帧](#showdelayshowminiframes)|显示或隐藏微型框架的窗口。|
|[CDocking管理器：：显示窗格](#showpanes)|显示或隐藏控件和自动隐藏栏的窗格。|
|[CDocking管理器：开始对接](#startsdocking)|根据智能对接管理器的对齐方式启动指定窗口的智能停靠。|
|[CDocking管理器：停止对接](#stopsdocking)|停止智能停靠。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CDocking管理器：m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|指定停靠管理器是否在 OLE 容器模式下隐藏窗格。|
|[CDocking管理器：：m_dockModeGlobal](#m_dockmodeglobal)|指定全局停靠模式。|
|[CDocking管理器：：m_nDockSensitivity](#m_ndocksensitivity)|指定停靠灵敏度。|
|[CDocking管理器：：m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|指定停靠窗格在直接停靠模式下停靠之前的时间（以毫秒为单位）。|
|[CDocking管理器：m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|指定工具栏停靠到主框架窗口之前的时间（以毫秒为单位）。|

## <a name="remarks"></a>备注

主框架窗口会自动创建并初始化此类。

停靠管理器对象包含停靠布局中所有窗格的列表，以及属于主框架窗口的所有[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)窗口的列表。

类`CDockingManager`实现一些服务，可用于查找窗格或`CPaneFrameWnd`窗口。 通常不直接调用这些服务，因为它们包装在主框架窗口对象中。 有关详细信息，请参阅[CPaneFramewnd 类](../../mfc/reference/cpaneframewnd-class.md)。

## <a name="customization-tips"></a>自定义提示

以下提示适用于`CDockingManager`对象：

- [CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)支持以下停靠模式：

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  这些停靠模式由[CDockingManager：：：m_dockModeGlobal](#m_dockmodeglobal)定义，并通过调用[CDockingManager：：setDockingMode](#setdockingmode)进行设置。

- 如果要创建非浮动、不可调整大小的窗格，请调用[CDockingManager：：AddPane](#addpane)方法。 此方法将窗格注册到负责窗格布局的停靠管理器。

## <a name="example"></a>示例

下面的示例演示如何在`CDockingManager`类中使用各种方法来配置`CDockingManager`对象。 该示例演示如何在所有停靠窗格的标题上显示打开弹出菜单的其他按钮，以及如何设置对象的停靠模式。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>要求

**标题：** afxDockingManager.h

## <a name="cdockingmanageradddocksite"></a><a name="adddocksite"></a>CDocking管理器：：添加Dock网站

创建停靠窗格并将其添加到控制栏列表中。

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>参数

info**<br/>
[在]对包含停靠窗格对齐的信息结构的引用。

*ppDockBar*<br/>
[出]指向指向新停靠窗格的指针。

### <a name="return-value"></a>返回值

如果成功创建了停靠窗格，则为 TRUE;如果成功创建了停靠窗格，则为 TRUE。否则。

## <a name="cdockingmanageraddhiddenmditabbedbar"></a><a name="addhiddenmditabbedbar"></a>CDocking管理器：：添加隐藏MDITabbedbar

将句柄添加到栏窗格到隐藏的 MDI 选项卡栏窗格列表中。

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向条形窗格的指针

## <a name="cdockingmanageraddpane"></a><a name="addpane"></a>CDocking管理器：：添加窗格

向停靠管理器注册窗格。

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[进出]指定要添加到停靠管理器的窗格。

*b泰尔*<br/>
[在]TRUE 将窗格添加到停靠管理器的窗格列表的末尾;否则，FALSE。

*bAutoHide*<br/>
[在]仅供内部使用。 始终使用默认值 FALSE。

*b 插入外边缘*<br/>
[在]仅供内部使用。 始终使用默认值 FALSE。

### <a name="return-value"></a>返回值

如果窗格已成功注册到停靠管理器，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

调用此方法与停靠管理器注册非浮动、不可调整大小的窗格。 如果不注册窗格，则在布局停靠管理器时，窗格将不会正确显示。

## <a name="cdockingmanageradjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDocking管理器：：调整停靠布局

重新计算和调整框架窗口中所有窗格的布局。

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>参数

*hdwp*<br/>
[在]指定延迟的窗口位置结构。 有关详细信息，请参阅 [Windows 数据类型](/windows/win32/WinProg/windows-data-types)。

### <a name="remarks"></a>备注

## <a name="cdockingmanageraddminiframe"></a><a name="addminiframe"></a>CDocking管理器：：添加Mini框架

将框架添加到迷你框架列表中。

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向帧的指针。

### <a name="return-value"></a>返回值

如果帧不在微型帧列表中并已成功添加，则为 TRUE;否则。

## <a name="cdockingmanageradjustpaneframes"></a><a name="adjustpaneframes"></a>CDocking 管理器：：调整窗格框架

使WM_NCCALCSIZE消息发送到所有窗格和`CPaneFrameWnd`窗口。

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

## <a name="cdockingmanageradjustrecttoclientarea"></a><a name="adjustrecttoclientarea"></a>Cdocking管理器：调整到客户端区域

调整矩形的对齐方式。

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>参数

*rectResult*<br/>
[在]对对象的引用`CRect`

*dwalignment*<br/>
[在]`CRect`对象的对齐方式

### <a name="return-value"></a>返回值

如果调整了对象的对齐方式，`CRect`则为 TRUE;否则。

### <a name="remarks"></a>备注

*dwalignment*参数可以具有以下值之一：

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

## <a name="cdockingmanageralignautohidepane"></a><a name="alignautohidepane"></a>CDocking管理器：对齐自动隐藏窗格

在自动隐藏模式下调整停靠窗格的大小，以便它占用帧的工作区的全宽或高度，并包围停靠站点。

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>参数

*p默认滑块*<br/>
[在]停靠滑块窗格。

*b可见*<br/>
[在]如果停靠窗格可见，则为 TRUE;如果停靠窗格可见，则为 TRUE。否则。

## <a name="cdockingmanagerautohidepane"></a><a name="autohidepane"></a>CDocking管理器：自动隐藏窗格

创建自动隐藏工具栏。

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向条形窗格的指针。

*pCurrAutoHideTool工具栏*<br/>
[在]指向自动隐藏工具栏的指针。

### <a name="return-value"></a>返回值

如果未创建自动隐藏工具栏，则为 NULL;如果未创建自动隐藏工具栏，则为 NULL。否则指向新工具栏的指针。

## <a name="cdockingmanagerbringbarstotop"></a><a name="bringbarstotop"></a>CDocking管理器：：带巴斯托托

将具有指定对齐的停靠条带到顶部。

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>参数

*dwalignment*<br/>
[在]带到其他窗口顶部的停靠条的对齐方式。

*b 排除已停靠条形*<br/>
[在]TRUE 以排除停靠的条形图位于顶部;否则 FALSE。

## <a name="cdockingmanagerbuildpanesmenu"></a><a name="buildpanesmenu"></a>CDocking管理器：：构建窗格菜单

将停靠窗格和工具栏的名称添加到菜单中。

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>参数

*菜单*<br/>
[在]要向其添加停靠窗格和工具栏名称的菜单。

*b工具栏*<br/>
[在]TRUE 仅向菜单添加工具栏名称;否则。

## <a name="cdockingmanagercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CDocking 管理器：：Calc预期多克已重新

计算停靠窗口的预期矩形。

```
void CalcExpectedDockedRect(
    CWnd* pWnd,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向要停靠的窗口的指针。

*ptMouse*<br/>
[在]鼠标位置。

*rectResult*<br/>
[出]计算的矩形。

*bDrawTab*<br/>
[在]TRUE 以绘制选项卡;否则 FALSE。

*ppTargetBar*<br/>
[出]指向目标窗格的指针。

### <a name="remarks"></a>备注

此方法计算当用户将窗口拖动到*ptMouse*指定的点并将其停靠在那里时，窗口将占用的矩形。

## <a name="cdockingmanagercreate"></a><a name="create"></a>CDocking管理器：创建

创建停靠管理器。

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
[在]指向停靠管理器的父帧的指针。 此值不能为 NULL。

### <a name="return-value"></a>返回值

永远真实。

## <a name="cdockingmanagerdeterminepaneandstatus"></a><a name="determinepaneandstatus"></a>CDocking管理器：:D

确定包含给定点的窗格及其停靠状态。

```
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,
    int nSensitivity,
    DWORD dwEnabledAlignment,
    CBasePane** ppTargetBar,
    const CBasePane* pBarToIgnore,
    const CBasePane* pBarToDock);
```

### <a name="parameters"></a>参数

*pt*<br/>
[在]要检查的窗格的位置。

*nSensitivity*<br/>
[在]要增加每个选中窗格的窗口矩形的值。 如果给定点位于此增加的区域中，则窗格满足搜索条件。

*启用对齐*<br/>
[在]停靠窗格的对齐方式。

*ppTargetBar*<br/>
[出]指向目标窗格的指针。

*pBartoignore*<br/>
[在]该方法忽略的窗格。

*pBartodock*<br/>
[在]停靠的窗格。

### <a name="return-value"></a>返回值

停靠状态。

### <a name="remarks"></a>备注

停靠状态可以是以下值之一：

|AFX_CS_STATUS值|含义|
|---------------------------|-------------|
|CS_NOTHING|指针不在停靠站点上。 因此，保持窗格浮动。|
|CS_DOCK_IMMEDIATELY|指针在即立模式下位于停靠站点上（DT_IMMEDIATE样式已启用），因此必须立即停靠窗格。|
|CS_DELAY_DOCK|指针位于另一个停靠窗格或主框架的边缘的停靠站点上。|
|CS_DELAY_DOCK_TO_TAB|指针位于停靠站点上，该站点会导致窗格停靠在选项卡式窗口中。 当鼠标位于另一个停靠窗格的标题上或选项卡式窗格的选项卡区域上时，将发生这种情况。|

## <a name="cdockingmanagerdisablerestoredockstate"></a><a name="disablerestoredockstate"></a>CDocking管理器：:D可还原DockDockState

启用或禁用从注册表加载停靠布局。

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>参数

*b禁用*<br/>
[在]TRUE 禁用从注册表加载停靠布局;否则，FALSE。

### <a name="remarks"></a>备注

在加载应用程序状态时必须保留停靠窗格和工具栏的当前布局时，请调用此方法。

## <a name="cdockingmanagerdockpane"></a><a name="dockpane"></a>CDocking管理器：:DockPane

将窗格停靠到另一个窗格或框架窗口。

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向要停靠的条形窗格的指针。

*nDockBarID*<br/>
[在]要停靠的条形的 ID。

*lpRect*<br/>
[在]目标矩形。

## <a name="cdockingmanagerdockpaneleftof"></a><a name="dockpaneleftof"></a>对接管理器：:D奥克帕内左

将窗格停靠到另一个窗格的左侧。

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>参数

*pBartodock*<br/>
[在]指向要停靠在*pTargetBar*左侧的窗格的指针。

*p目标栏*<br/>
[在]指向目标窗格的指针。

### <a name="return-value"></a>返回值

如果窗格已成功停靠，则为 TRUE;如果窗格已成功停靠。否则，FALSE。

## <a name="cdockingmanagerenableautohidepanes"></a><a name="enableautohidepanes"></a>CDocking 管理器：启用自动隐藏窗格

启用窗格与主框架的停靠，创建停靠窗格，并将其添加到控制栏列表中。

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
[在]停靠对齐。

### <a name="return-value"></a>返回值

如果成功创建了停靠窗格，则为 TRUE;如果成功创建了停靠窗格，则为 TRUE。否则。

## <a name="cdockingmanagerenabledocking"></a><a name="enabledocking"></a>CDocking管理器：启用对接

创建停靠窗格，并使窗格与主框架对接。

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
[在]停靠对齐。

### <a name="return-value"></a>返回值

如果成功创建了停靠窗格，则为 TRUE;如果成功创建了停靠窗格，则为 TRUE。否则。

## <a name="cdockingmanagerenabledocksitemenu"></a><a name="enabledocksitemenu"></a>CDocking管理器：启用DockSite菜单

显示一个附加按钮，该按钮在所有停靠窗格的标题上打开一个弹出式菜单。

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 启用停靠站点菜单;否则，FALSE。

### <a name="remarks"></a>备注

停靠站点菜单显示以下选项，用于更改窗格的停靠状态：

- `Floating`- 浮动窗格

- `Docking`- 将窗格停靠在窗格上次停靠的位置的主框架上

- `AutoHide`- 将窗格切换到自动隐藏模式

- `Hide`- 隐藏窗格

默认情况下，不显示此菜单。

## <a name="cdockingmanagerenablepanecontextmenu"></a><a name="enablepanecontextmenu"></a>CDocking管理器：：启用窗格上下文菜单

告诉库显示一个特殊的上下文菜单，该菜单具有应用程序工具栏和停靠窗格的列表，当用户单击鼠标右键并且库正在处理WM_CONTEXTMENU消息时。

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]如果为 TRUE，库将打开对自动上下文菜单的支持;如果为 TRUE，则库将打开对自动上下文菜单的支持。如果 FALSE 库关闭对自动上下文菜单的支持。

*ui 定制Cmd*<br/>
[在]菜单中 **"自定义**"项的命令 ID。

*str定制文本*<br/>
[在]**自定义**项的文本。

*b工具栏*<br/>
[在]如果为 TRUE，则菜单仅显示应用程序工具栏的列表;如果为 TRUE，则菜单仅显示应用程序工具栏的列表。如果 FALSE，库将应用程序停靠窗格添加到此列表。

## <a name="cdockingmanagerfinddocksite"></a><a name="finddocksite"></a>CDocking管理器：：查找DockSite

检索位于指定位置且具有指定对齐方式的条形窗格。

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>参数

*dwalignment*<br/>
[在]条形窗格的对齐方式。

*b外部*<br/>
[在]如果为 TRUE，则检索控制栏列表中头部位置的条形。 否则，在控制条列表中检索尾部位置的条。

### <a name="return-value"></a>返回值

具有指定对齐方式的停靠窗格;否则为 NULL。

## <a name="cdockingmanagerfindpanebyid"></a><a name="findpanebyid"></a>CDocking管理器：：查找PaneByID

按指定的控件 ID 查找窗格。

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>参数

*乌巴里德*<br/>
[在]指定要查找的窗格的控制 ID。

*b搜索迷你框架*<br/>
[在]TRUE 以包括搜索中的所有浮动窗格。 FALSE 只包括停靠的窗格。

### <a name="return-value"></a>返回值

具有指定控件 ID 的[CBasePane](../../mfc/reference/cbasepane-class.md)对象，如果找不到指定的窗格，则为 NULL。

### <a name="remarks"></a>备注

## <a name="cdockingmanagerfinddocksitebypane"></a><a name="finddocksitebypane"></a>CDocking管理器：：查找DocksitebyPane

返回具有目标栏窗格 ID 的条形窗格。

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>参数

*p目标栏*<br/>
[在]指向目标栏窗格的指针。

### <a name="return-value"></a>返回值

具有目标栏窗格 ID 的栏窗格;如果没有此类条形窗格，则 NULL。

## <a name="cdockingmanagerfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDocking管理器：修复虚拟重新

将所有当前工具栏位置提交到虚拟矩形。

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>备注

当用户开始拖动工具栏时，应用程序会记住其*在虚拟矩形*中的原始位置。 当用户在其停靠站点上移动工具栏时，工具栏可能会移动其他工具栏。 其他工具栏的原始位置存储在相应的虚拟矩形中。

## <a name="cdockingmanagerframefrompoint"></a><a name="framefrompoint"></a>CDocking管理器：：从点帧

返回包含给定点的帧。

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
[在]指定要检查的点（在屏幕坐标中）。

*pFrame 排除*<br/>
[在]指向要排除的帧的指针。

*b 浮动多只*<br/>
[在]TRUE 以排除不是 的 实例的`CMultiPaneFrameWnd`帧。否则。

### <a name="return-value"></a>返回值

包含给定点的帧;否则为 NULL。

## <a name="cdockingmanagergetclientareabounds"></a><a name="getclientareabounds"></a>CDocking 管理器：获取客户区域绑定

获取包含工作区边界的矩形。

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>参数

*rcClient*<br/>
[出]对包含工作区边界的矩形的引用。

### <a name="return-value"></a>返回值

包含工作区边界的矩形。

## <a name="cdockingmanagergetdockingmode"></a><a name="getdockingmode"></a>CDocking管理器：获取对接模式

返回当前停靠模式。

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>返回值

表示当前停靠模式的枚举器值。 可以为下列值之一：

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>备注

要设置停靠模式，请致电[CdockingManager：：设置停靠模式](#setdockingmode)。

## <a name="cdockingmanagergetdocksiteframewnd"></a><a name="getdocksiteframewnd"></a>CDocking管理器：：获取DockSiteFramewnd

获取指向父窗口框架的指针。

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>返回值

指向父窗口框架的指针。

## <a name="cdockingmanagergetenabledautohidealignment"></a><a name="getenabledautohidealignment"></a>Cdocking 管理器：实现启用自动隐藏对齐

返回窗格的启用对齐方式。

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>返回值

如果未启用自动隐藏窗格，则CBRS_ALIGN_标志或 0 的位组合。 有关详细信息，请参阅[CFramewnd：：启用停靠](../../mfc/reference/cframewnd-class.md#enabledocking)。

### <a name="remarks"></a>备注

该方法返回自动隐藏控制栏的启用对齐方式。 要启用自动隐藏栏，请致电[CFramewndEx：：启用自动隐藏窗格](../../mfc/reference/cframewndex-class.md#enableautohidepanes)。

## <a name="cdockingmanagergetminiframes"></a><a name="getminiframes"></a>CDocking管理器：获取迷你框架

获取微型帧列表。

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>返回值

包含属于停靠管理器的控制栏的小型帧列表。

## <a name="cdockingmanagergetouteredgebounds"></a><a name="getouteredgebounds"></a>CDocking管理器：获取外部边缘绑定

获取包含框架外边缘的矩形。

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>返回值

包含框架外边缘的矩形。

## <a name="cdockingmanagergetpanelist"></a><a name="getpanelist"></a>CDocking管理器：获取窗格列表

返回属于停靠管理器的窗格列表。 这包括所有浮动窗格。

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>参数

*lstBars*<br/>
[进出]包含当前停靠管理器的所有窗格。

*bInclude 自动隐藏*<br/>
[在]TRUE 以包括处于自动隐藏模式的窗格;否则，FALSE。

*pRTC过滤器*<br/>
[在]如果不是 NULL，则返回的列表仅包含指定运行时类的窗格。

*bIncludeTabs*<br/>
[在]TRUE 以包括选项卡;否则，FALSE。

### <a name="remarks"></a>备注

如果停靠管理器中有任何选项卡式窗格，该方法将返回指向[CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)对象的指针，并且必须显式枚举选项卡。

使用*pRTCFilter*获取特定类的窗格。 例如，您可以通过适当设置此值来仅获取工具栏。

## <a name="cdockingmanagergetsmartdockingmanager"></a><a name="getsmartdockingmanager"></a>CDocking管理器：获取智能扩展管理器

检索指向智能停靠管理器的指针。

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>返回值

指向智能停靠管理器的指针。

## <a name="cdockingmanagergetsmartdockingmanagerpermanent"></a><a name="getsmartdockingmanagerpermanent"></a>CDocking管理器：获取智能扩展管理器永久

检索指向智能停靠管理器的指针。

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>返回值

指向智能停靠管理器的指针。

## <a name="cdockingmanagergetsmartdockingparams"></a><a name="getsmartdockingparams"></a>CDocking管理器：获取智能对接参数

返回停靠管理器的智能停靠参数。

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>返回值

包含当前停靠管理器的智能停靠参数的类。 有关详细信息，请参阅[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)。

### <a name="remarks"></a>备注

## <a name="cdockingmanagerhideautohidepanes"></a><a name="hideautohidepanes"></a>CDocking管理器：隐藏自动隐藏窗格

隐藏处于自动隐藏模式的窗格。

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>参数

*pBarto排除*<br/>
[在]指向要从隐藏中排除的条形的指针。

*b 立即*<br/>
[在]TRUE 立即隐藏窗格;FALSE 以隐藏具有自动隐藏效果的窗格。

## <a name="cdockingmanagerinsertdocksite"></a><a name="insertdocksite"></a>CDocking管理器：：插入DockSite

创建停靠窗格并将其插入控制栏列表。

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>参数

info**<br/>
[在]包含有关停靠窗格的对齐信息的结构。

*dwalignto 插入后*<br/>
[在]停靠窗格的对齐方式。

*ppDockBar*<br/>
[出]指向指向停靠窗格的指针。

### <a name="return-value"></a>返回值

如果成功创建了停靠窗格，则为 TRUE;如果成功创建了停靠窗格，则为 TRUE。否则。

## <a name="cdockingmanagerinsertpane"></a><a name="insertpane"></a>CDocking管理器：插入窗格

将控制窗格插入控制栏列表中。

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>参数

*p控制栏*<br/>
[在]指向控件窗格的指针。

*p目标*<br/>
[在]指向目标窗格的指针。

*b 后*<br/>
[在]TRUE 在目标窗格的位置后插入窗格;否则。

### <a name="return-value"></a>返回值

如果控制窗格已成功添加到控制栏列表中，则为 TRUE;如果控制窗格已成功添加到控制栏列表中，则为 TRUE。否则。

### <a name="remarks"></a>备注

如果控制窗格已在控制栏列表中，或者控制栏列表中不存在目标窗格，则此方法将返回 false。

## <a name="cdockingmanagerisdocksitemenu"></a><a name="isdocksitemenu"></a>CDocking管理器：：IsDockSiteMenu

指定弹出菜单是否显示在所有窗格的标题上。

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>返回值

如果停靠站点菜单显示在所有停靠窗格的标题上，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

您可以通过调用[CDockingManager：：启用DockSiteMenu](#enabledocksitemenu)来启用扩展站点菜单。

## <a name="cdockingmanagerisinadjustlayout"></a><a name="isinadjustlayout"></a>Cdocking 管理器：正在调整布局

确定是否调整了所有窗格的布局。

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>返回值

如果调整了所有窗格的布局，则为 TRUE;如果调整了所有窗格的布局。否则。

## <a name="cdockingmanagerisolecontainermode"></a><a name="isolecontainermode"></a>CDocking管理器：isOLE容器模式

指定停靠管理器是否处于 OLE 容器模式。

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>返回值

如果停靠管理器处于 OLE 容器模式，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

在 OLE 容器模式下，所有停靠窗格和应用程序工具栏都处于隐藏状态。 如果将[CDockingManager：：m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)设置为 TRUE，则窗格也会在此模式下隐藏。

## <a name="cdockingmanagerispointneardocksite"></a><a name="ispointneardocksite"></a>CDocking管理器：：IsPointNearDockSite

确定指定点是否靠近停靠站点。

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[在]指定的点。

*dwBaralignment*<br/>
[出]指定点附近的边。 可能的值是CBRS_ALIGN_LEFT、CBRS_ALIGN_RIGHT、CBRS_ALIGN_TOP 和CBRS_ALIGN_BOTTOM。

*bouterEdge*<br/>
[出]如果点靠近停靠站点的外部边界，则为 TRUE;否则。

### <a name="return-value"></a>返回值

如果点靠近停靠站点，则为 TRUE;否则 FALSE。

## <a name="cdockingmanagerisprintpreviewvalid"></a><a name="isprintpreviewvalid"></a>CDocking管理器：：正在打印预览有效

确定是否设置了打印预览模式。

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>返回值

如果设置了打印预览模式，则为 TRUE;如果已设置打印预览模式，则为 TRUE。否则。

## <a name="cdockingmanagerloadstate"></a><a name="loadstate"></a>CDocking管理器：加载状态

从注册表加载停靠管理器的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]配置文件名称。

*uiID*<br/>
[在]停靠管理器的 ID。

### <a name="return-value"></a>返回值

如果停靠管理器状态已成功加载，则为 TRUE;如果停靠管理器状态已成功加载，则为 TRUE。否则 FALSE。

## <a name="cdockingmanagerlockupdate"></a><a name="lockupdate"></a>CDocking管理器：锁更新

锁定给定的窗口。

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>参数

*块*<br/>
[在]如果窗口已锁定，则为 TRUE;否则。

### <a name="remarks"></a>备注

当窗口被锁定时，它不能移动，也不能重绘。

## <a name="cdockingmanagerm_bhidedockingbarsincontainermode"></a><a name="m_bhidedockingbarsincontainermode"></a>CDocking管理器：m_bHideDockingBarsInContainerMode

指定停靠管理器是否在 OLE 容器模式下隐藏窗格。

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>备注

如果要使所有窗格停靠在主机架上，当应用程序处于 OLE 容器模式时，将此值设置为 FALSE。 默认情况下，此值为 TRUE。

## <a name="cdockingmanagerm_dockmodeglobal"></a><a name="m_dockmodeglobal"></a>CDocking管理器：：m_dockModeGlobal

指定全局停靠模式。

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>备注

默认情况下，每个停靠窗格都使用此停靠模式。 有关此字段可以设置为的值的详细信息，请参阅[CBasePane：：获取停靠模式](../../mfc/reference/cbasepane-class.md#getdockingmode)。

## <a name="cdockingmanagerm_ndocksensitivity"></a><a name="m_ndocksensitivity"></a>CDocking管理器：：m_nDockSensitivity

指定停靠灵敏度。

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>备注

停靠敏感度定义在框架将其状态更改为停靠之前，浮动窗格可以接近停靠窗格、停靠站点或其他窗格的接近程度。

## <a name="cdockingmanagerm_ntimeoutbeforedockingbardock"></a><a name="m_ntimeoutbeforedockingbardock"></a>CDocking管理器：：m_nTimeOutBeforeDockingBarDock

指定停靠窗格在直接停靠模式下停靠之前的时间（以毫秒为单位）。

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>备注

在停靠窗格之前，框架将等待指定的时间长度。 这样可以防止在用户仍在拖动窗格时意外停靠到该位置。

## <a name="cdockingmanagerm_ntimeoutbeforetoolbardock"></a><a name="m_ntimeoutbeforetoolbardock"></a>CDocking管理器：m_nTimeOutBeforeToolBarDock

指定工具栏停靠到主框架窗口之前的时间（以毫秒为单位）。

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>备注

在停靠工具栏之前，框架将等待指定的时间长度。 这样可以防止工具栏在用户仍在拖动时意外停靠到该位置。

## <a name="cdockingmanageronactivateframe"></a><a name="onactivateframe"></a>CDocking管理器：在激活帧上

当框架窗口变为活动或停用时，由框架调用。

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>参数

*b 激活*<br/>
[在]如果为 TRUE，则框架窗口将变为活动状态;如果为 TRUE，则框架窗口将变为活动状态。如果 FALSE，则框架窗口将停用。

## <a name="cdockingmanageronclosepopupmenu"></a><a name="onclosepopupmenu"></a>CDocking管理器：：上接合弹出菜单

当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>备注

框架在即将关闭当前主窗口时发送WM_DESTROY消息。 重写此方法，以处理`CMFCPopupMenu``CMFCPopupMenu`对象处理WM_DESTROY消息时属于帧窗口的对象的通知。

## <a name="cdockingmanageronmoveminiframe"></a><a name="onmoveminiframe"></a>Cdocking管理器：在移动迷你框架

由框架调用以移动微型框架窗口。

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>参数

*pFrame*<br/>
[在]指向微型框架窗口的指针。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

## <a name="cdockingmanageronpanecontextmenu"></a><a name="onpanecontextmenu"></a>Cdocking管理器：：在窗格上下文菜单

当框架生成包含窗格列表的菜单时，由框架调用。

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]指定菜单的位置。

## <a name="cdockingmanagerpanefrompoint"></a><a name="panefrompoint"></a>CDocking管理器：:P从点

返回包含给定点的窗格。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar = false,
    CRuntimeClass* pRTCBarType = NULL,
    BOOL bCheckVisibility = FALSE,
    const CBasePane* pBarToIgnore = NULL) const;

virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType = NULL,
    const CBasePane* pBarToIgnore = NULL) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[在]指定要检查的点（在屏幕坐标中）。

*nSensitivity*<br/>
[在]要膨胀每个选中窗格的窗口矩形的值。 如果给定点位于此膨胀区域中，则窗格满足搜索条件。

*bExactBar*<br/>
[在]TRUE 忽略*n 敏感参数*;否则，FALSE。

*pRTCBar类型*<br/>
[在]如果不是 NULL，该方法将仅搜索指定类型的窗格。

*b 检查可见性*<br/>
[在]TRUE 仅检查可见窗格;否则，FALSE。

*dwalignment*<br/>
[出]如果在指定点找到窗格，则此参数包含最接近指定点的窗格的一侧。 有关详细信息，请参见“备注”部分。

*pBartoignore*<br/>
[在]如果不是 NULL，该方法将忽略此参数指定的窗格。

### <a name="return-value"></a>返回值

包含给定点的[CBasePane](../../mfc/reference/cbasepane-class.md)派生对象，如果没有找到窗格，则为 NULL。

### <a name="remarks"></a>备注

当函数返回并找到窗格时 *，dwAlignment*包含指定点的对齐方式。 例如，如果点最接近窗格的顶部，*则 dwAlignment*设置为CBRS_ALIGN_TOP。

## <a name="cdockingmanagerprocesspanecontextmenucommand"></a><a name="processpanecontextmenucommand"></a>CDocking管理器：:ProcessPane上下文菜单命令

由框架调用以选择或清除指定命令的复选框，并重新计算显示的窗格的布局。

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]菜单中控制栏的 ID。

*n代码*<br/>
[在]命令通知代码。

*pExtra*<br/>
[在]如果*nCode* CN_UPDATE_COMMAND_UI，则指向 void`CCmdUI`的指针，该指针将转换为指向指向的指针。

*pHandlerInfo*<br/>
[在]指向信息结构的指针。 未使用此参数。

### <a name="return-value"></a>返回值

如果*pEXtra*不是 NULL，*并且 nCode*等于CN_UPDATE_COMMAND_UI，或者如果有一个带有指定*nID 的控制*栏，则为 TRUE。

## <a name="cdockingmanagerrecalclayout"></a><a name="recalclayout"></a>CDocking管理器：Recalclayout

重新计算控件列表中存在的控件的内部布局。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

*b 通知*<br/>
[在]不使用此参数。

## <a name="cdockingmanagerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CDocking 管理器：：释放空窗格容器

释放空窗格容器。

```
void ReleaseEmptyPaneContainers();
```

## <a name="cdockingmanagerremovehiddenmditabbedbar"></a><a name="removehiddenmditabbedbar"></a>CDocking 管理器：：删除隐藏 MDITabbedbar

删除指定的隐藏栏窗格。

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向要删除的条形窗格的指针。

## <a name="cdockingmanagerremoveminiframe"></a><a name="removeminiframe"></a>CDocking管理器：删除Mini框架

从迷你框架列表中删除指定的帧。

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向要删除的帧的指针。

### <a name="return-value"></a>返回值

如果删除了指定的帧，则为 TRUE;如果已删除指定的帧否则。

## <a name="cdockingmanagerremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CDockManager：从Dock管理器中删除窗格

取消注册窗格并将其从停靠管理器中的列表中删除。

```
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向要删除的窗格的指针。

*b破坏*<br/>
[在]如果为 TRUE，则删除的窗格将被销毁。

*b 调整布局*<br/>
[在]如果为 TRUE，请立即调整停靠布局。

*bAutoHide*<br/>
[在]如果为 TRUE，则窗格将从自动隐藏栏列表中删除。 如果 FALSE，则窗格将从常规窗格列表中删除。

*pBar 替换*<br/>
[在]指向替换已删除窗格的窗格的指针。

## <a name="cdockingmanagerreplacepane"></a><a name="replacepane"></a>CDocking管理器：替换窗格

用一个窗格替换另一个窗格。

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>参数

*p 原始栏*<br/>
[在]指向原始窗格的指针。

*pNewBar*<br/>
[在]指向替换原始窗格的窗格的指针。

### <a name="return-value"></a>返回值

如果已成功替换窗格，则为 TRUE;如果窗格已成功替换，则为 TRUE。否则。

## <a name="cdockingmanagerresortminiframesforzorder"></a><a name="resortminiframesforzorder"></a>CDocking管理器：：度假村迷你框架为ZOrder

在迷你帧列表中对帧进行设置。

```
void ResortMiniFramesForZOrder();
```

## <a name="cdockingmanagersavestate"></a><a name="savestate"></a>CDocking管理器：：保存状态

将停靠管理器的状态保存到注册表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]注册表项的路径。

*uiID*<br/>
[在]停靠管理器 ID。

### <a name="return-value"></a>返回值

如果成功保存状态，则为 TRUE;如果状态已成功保存，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

将停靠管理器的状态保存到注册表涉及保存控制栏的状态、自动隐藏栏的状态以及停靠管理器中存在的微型帧的状态。

## <a name="cdockingmanagersendmessagetominiframes"></a><a name="sendmessagetominiframes"></a>CDocking管理器：：发送消息到微型帧

将指定的消息发送到所有微型帧。

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>参数

*u消息*<br/>
[在]要发送的消息。

*wParam*<br/>
[在]其他邮件相关信息。

*lParam*<br/>
[在]其他邮件相关信息。

### <a name="return-value"></a>返回值

永远真实。

## <a name="cdockingmanagerserialize"></a><a name="serialize"></a>CDocking管理器：序列化

将停靠管理器写入存档。

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
[在]对存档对象的引用。

### <a name="remarks"></a>备注

将停靠管理器写入存档涉及确定停靠控制栏和滑块的数量，并将控制栏、迷你框架、自动隐藏栏和 MDI 选项卡栏写入存档。

## <a name="cdockingmanagersetautohidezorder"></a><a name="setautohidezorder"></a>CDocking 管理器：设置自动隐藏顺序

设置控制栏和指定窗格的大小、宽度和高度。

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>参数

*pAHDockingBar*<br/>
[在]指向可停靠窗格的指针。

## <a name="cdockingmanagersetdockingmode"></a><a name="setdockingmode"></a>CDocking管理器：设置对接模式

设置停靠模式。

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>参数

*坞站模式*<br/>
指定新的停靠模式。 有关详细信息，请参见“备注”部分。

*主题*<br/>
指定用于智能停靠标记的主题。 它可以是以下枚举值之一：AFX_SDT_DEFAULT、AFX_SDT_VS2005、AFX_SDT_VS2008。

### <a name="remarks"></a>备注

调用此静态方法以设置停靠模式。

*dockMode*可以是以下值之一：

- DT_STANDARD - 可视化工作室 2003 中实现的标准停靠模式。 在没有拖动上下文的情况下拖动窗格。

- DT_IMMEDIATE - 在 Microsoft Visio 中实现的即时停靠模式。 窗格使用拖动上下文拖动，但不会显示任何标记。

- DT_SMART - Visual Studio 2005 中实现的智能对接模式。 使用拖动上下文拖动窗格，并显示显示窗格停靠位置的智能标记。

## <a name="cdockingmanagersetdockstate"></a><a name="setdockstate"></a>CDocking管理器：：SetDockState

设置控制栏、微型框架和自动隐藏栏的停靠状态。

```
virtual void SetDockState();
```

## <a name="cdockingmanagersetprintpreviewmode"></a><a name="setprintpreviewmode"></a>CDocking管理器：：设置打印预览模式

设置打印预览中显示的条形图的打印预览模式。

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>参数

*b预览*<br/>
[在]如果设置了打印预览模式，则为 TRUE;如果已设置打印预览模式，则为 TRUE。否则。

*pState*<br/>
[在]指向预览状态的指针。 未使用此参数。

## <a name="cdockingmanagersetsmartdockingparams"></a><a name="setsmartdockingparams"></a>CDocking管理器：设置智能对接参数

设置定义智能停靠行为的参数。

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>参数

*params*<br/>
[进出]定义智能停靠的参数。

### <a name="remarks"></a>备注

如果要自定义智能停靠标记的外观、颜色或形状，请调用此方法。

要使用智能停靠标记的默认查找，请将[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)的未初始化实例传递给*参数*。

## <a name="cdockingmanagershowdelayshowminiframes"></a><a name="showdelayshowminiframes"></a>CDocking管理器：：显示延迟显示迷你帧

显示或隐藏微型框架的窗口。

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]TRUE 使显示的帧的窗口处于活动状态;FALSE 以隐藏框架的窗口。

## <a name="cdockingmanagershowpanes"></a><a name="showpanes"></a>CDocking管理器：：显示窗格

显示或隐藏控件和自动隐藏栏的窗格。

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]TRUE 以显示窗格;FALSE 以隐藏窗格。

### <a name="return-value"></a>返回值

始终为 FALSE。

## <a name="cdockingmanagerstartsdocking"></a><a name="startsdocking"></a>CDocking管理器：开始对接

根据智能对接管理器的对齐方式启动指定窗口的智能停靠。

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>参数

*pDockingwnd*<br/>
[在]指向要停靠的窗口的指针。

## <a name="cdockingmanagerstopsdocking"></a><a name="stopsdocking"></a>CDocking管理器：停止对接

停止智能停靠。

```
void StopSDocking();
```

## <a name="cdockingmanagergetsmartdockingtheme"></a><a name="getsmartdockingtheme"></a>CDocking管理器：获取智能对接主题

返回用于显示智能停靠标记的主题的静态方法。

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>返回值

返回以下枚举值之一：AFX_SDT_DEFAULT、AFX_SDT_VS2005、AFX_SDT_VS2008。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFramewnd 类](../../mfc/reference/cpaneframewnd-class.md)
