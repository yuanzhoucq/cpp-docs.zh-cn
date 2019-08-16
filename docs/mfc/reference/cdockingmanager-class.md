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
ms.openlocfilehash: 8709b3a4eb3f57a3d2700ad7aaed16df994245c5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506872"
---
# <a name="cdockingmanager-class"></a>CDockingManager 类

实现用于控制主框架窗口中停靠布局的核心功能。

## <a name="syntax"></a>语法

```
class CDockingManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|创建停靠窗格, 并将其添加到控件条列表。|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|将图柄添加到隐藏的 MDI 选项卡式条形图窗格的列表中。|
|[CDockingManager::AddMiniFrame](#addminiframe)|将帧添加到袖珍帧列表。|
|[CDockingManager::AddPane](#addpane)|向停靠管理器注册窗格。|
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|重新计算并调整框架窗口中所有窗格的布局。|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|使 WM_NCCALCSIZE 消息发送到所有窗格和`CPaneFrameWnd`窗口。|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|调整矩形的对齐方式。|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|在自动隐藏模式下调整停靠窗格的大小, 使其采用停靠站点周围的框架工作区的完整宽度或高度。|
|[CDockingManager::AutoHidePane](#autohidepane)|创建自动隐藏工具栏。|
|[CDockingManager::BringBarsToTop](#bringbarstotop)|将具有指定对齐方式的停靠栏引入到顶部。|
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|将停靠窗格和工具栏的名称添加到菜单中。|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|计算停靠窗口的预期矩形。|
|[CDockingManager::Create](#create)|创建扩展管理器。|
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|确定包含给定点及其停靠状态的窗格。|
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|启用或禁用从注册表加载停靠布局。|
|[CDockingManager::DockPane](#dockpane)|将一个窗格停靠到另一个窗格或框架窗口。|
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|将窗格停靠到另一个窗格的左侧。|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|允许将窗格停靠到主框架, 创建停靠窗格, 并将其添加到控件条列表。|
|[CDockingManager::EnableDocking](#enabledocking)|创建停靠窗格, 并使窗格停靠在主框架中。|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|显示一个附加按钮, 该按钮打开所有停靠窗格标题上的弹出菜单。|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|当用户单击鼠标右键并且库正在处理 WM_CONTEXTMENU 消息时, 通知库显示具有应用程序工具栏和停靠窗格列表的特定上下文菜单。|
|[CDockingManager::FindDockSite](#finddocksite)|检索位于指定位置并且具有指定对齐方式的栏窗格。|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|返回具有目标栏窗格 id 的栏窗格。|
|[CDockingManager::FindPaneByID](#findpanebyid)|按指定的控件 ID 查找窗格。|
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|将所有当前工具栏位置提交到虚拟矩形。|
|[CDockingManager::FrameFromPoint](#framefrompoint)|返回包含给定点的帧。|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|获取包含工作区的边界的矩形。|
|[CDockingManager::GetDockingMode](#getdockingmode)|返回当前停靠模式。|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|获取指向父窗口框架的指针。|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|返回已启用的窗格对齐方式。|
|[CDockingManager::GetMiniFrames](#getminiframes)|获取 miniframes 的列表。|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|获取一个矩形, 其中包含框架的外边缘。|
|[CDockingManager::GetPaneList](#getpanelist)|返回属于停靠管理器的窗格的列表。 这包括所有浮动窗格。|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|检索指向智能停靠管理器的指针。|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|检索指向智能停靠管理器的指针。|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|返回停靠管理器的智能停靠参数。|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|返回用于显示智能停靠标记的主题的静态方法。|
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|隐藏处于自动隐藏模式下的窗格。|
|[CDockingManager::InsertDockSite](#insertdocksite)|创建停靠窗格, 并将其插入到控件条列表中。|
|[CDockingManager::InsertPane](#insertpane)|将控件窗格插入到控件条列表中。|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|指定是否在所有窗格的标题上显示弹出菜单。|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|确定是否调整所有窗格的布局。|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|指定停靠管理器是否处于 OLE 容器模式。|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|确定指定点是否在停靠站点附近。|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|确定是否设置了 "打印预览" 模式。|
|[CDockingManager::LoadState](#loadstate)|从注册表加载停靠管理器的状态。|
|[CDockingManager::LockUpdate](#lockupdate)|锁定给定的窗口。|
|[CDockingManager::OnActivateFrame](#onactivateframe)|当框架窗口被激活或停用时由框架调用。|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|由框架调用以移动微型框架窗口。|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|当框架生成包含窗格列表的菜单时由框架调用。|
|[CDockingManager::PaneFromPoint](#panefrompoint)|返回包含给定点的窗格。|
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|由框架调用以选择或清除指定命令的复选框, 并重新计算显示的窗格的布局。|
|[CDockingManager::RecalcLayout](#recalclayout)|重新计算控件列表中存在的控件的内部布局。|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|释放空窗格容器。|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|删除指定的隐藏栏窗格。|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|从微型帧列表中删除指定的帧。|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|取消注册窗格, 并将其从停靠管理器的列表中删除。|
|[CDockingManager::ReplacePane](#replacepane)|用一个窗格替换另一个窗格。|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|在小型帧列表中滑雪场帧。|
|[CDockingManager::SaveState](#savestate)|将停靠管理器的状态保存到注册表中。|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|向所有微型帧发送指定的消息。|
|[CDockingManager::Serialize](#serialize)|将扩展管理器写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|设置控件条和指定窗格的大小、宽度和高度。|
|[CDockingManager::SetDockingMode](#setdockingmode)|设置停靠模式。|
|[CDockingManager::SetDockState](#setdockstate)|设置控制条、微型帧和自动隐藏栏的停靠状态。|
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|设置打印预览中显示的条形的打印预览模式。|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|设置用于定义智能停靠行为的参数。|
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|显示或隐藏微型框架的窗口。|
|[CDockingManager::ShowPanes](#showpanes)|显示或隐藏控件窗格和自动隐藏栏。|
|[CDockingManager::StartSDocking](#startsdocking)|根据智能停靠管理器的对齐方式, 启动指定窗口的智能停靠。|
|[CDockingManager::StopSDocking](#stopsdocking)|停止智能停靠。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|指定停靠管理器是否在 OLE 容器模式下隐藏窗格。|
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|指定全局停靠模式。|
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|指定停靠敏感度。|
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|指定停靠窗格在直接停靠模式下停靠之前的时间 (以毫秒为单位)。|
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|指定工具栏停靠在主框架窗口之前的时间 (以毫秒为单位)。|

## <a name="remarks"></a>备注

主框架窗口将自动创建并初始化此类。

停靠管理器对象包含停靠布局中所有窗格的列表, 还包含属于主框架窗口的所有[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)窗口的列表。

类实现某些可用于查找窗格`CPaneFrameWnd`或窗口的服务。 `CDockingManager` 通常不会直接调用这些服务, 因为它们被包装在主框架窗口对象中。 有关详细信息, 请参阅[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)。

## <a name="customization-tips"></a>自定义提示

以下提示适用于`CDockingManager`对象:

- [CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)支持以下停靠模式:

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  这些停靠模式由[CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal)定义, 并通过调用[CDockingManager:: SetDockingMode](#setdockingmode)来设置。

- 若要创建非浮动、不可调整大小的窗格, 请调用[CDockingManager:: AddPane](#addpane)方法。 此方法向停靠管理器注册窗格, 后者负责窗格的布局。

## <a name="example"></a>示例

下面的示例演示如何使用类中的`CDockingManager`各种方法`CDockingManager`配置对象。 该示例演示如何显示一个附加按钮, 该按钮打开所有停靠窗格标题上的弹出菜单, 以及如何设置对象的停靠模式。 此代码片段是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>要求

**标头:** afxDockingManager

##  <a name="adddocksite"></a>CDockingManager::AddDockSite

创建停靠窗格, 并将其添加到控件条列表。

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>参数

info<br/>
中对包含停靠窗格对齐的信息结构的引用。

*ppDockBar*<br/>
弄指向新的停靠窗格指针的指针。

### <a name="return-value"></a>返回值

如果已成功创建停靠窗格, 则为 TRUE;否则为 FALSE。

##  <a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar

将图柄添加到隐藏的 MDI 选项卡式条形图窗格的列表中。

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

*pBar*<br/>
中指向条形窗格的指针

##  <a name="addpane"></a>CDockingManager::AddPane

向停靠管理器注册窗格。

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in, out]指定要添加到停靠管理器的窗格。

*bTail*<br/>
中若要将窗格添加到停靠管理器的窗格列表的末尾, 则为 TRUE;否则为 FALSE。

*bAutoHide*<br/>
中仅供内部使用。 始终使用默认值 FALSE。

*bInsertForOuterEdge*<br/>
中仅供内部使用。 始终使用默认值 FALSE。

### <a name="return-value"></a>返回值

如果窗格已成功注册到停靠管理器, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法可将非浮动、不可调整大小的窗格注册到停靠管理器。 如果未注册窗格, 则当定位管理器被布局时, 它们将不会正确显示。

##  <a name="adjustdockinglayout"></a>CDockingManager:: AdjustDockingLayout

重新计算并调整框架窗口中所有窗格的布局。

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>参数

*hdwp*<br/>
中指定延迟的窗口位置结构。 有关详细信息，请参阅 [Windows 数据类型](/windows/win32/WinProg/windows-data-types)。

### <a name="remarks"></a>备注

##  <a name="addminiframe"></a>CDockingManager::AddMiniFrame

将帧添加到袖珍帧列表。

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向帧的指针。

### <a name="return-value"></a>返回值

如果框架不在小型框架列表中并且已成功添加, 则为 TRUE;否则为 FALSE。

##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames

使 WM_NCCALCSIZE 消息发送到所有窗格和`CPaneFrameWnd`窗口。

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

##  <a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea

调整矩形的对齐方式。

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>参数

*rectResult*<br/>
中对`CRect`对象的引用

*dwAlignment*<br/>
中`CRect`对象的对齐方式

### <a name="return-value"></a>返回值

如果调整`CRect`对象的对齐方式, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

*DwAlignment*参数可以具有下列值之一:

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

##  <a name="alignautohidepane"></a>  CDockingManager::AlignAutoHidePane

在自动隐藏模式下调整停靠窗格的大小, 使其采用停靠站点周围的框架工作区的完整宽度或高度。

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>参数

*pDefaultSlider*<br/>
中停靠滑块窗格。

*bIsVisible*<br/>
中如果停靠窗格可见, 则为 TRUE;否则为 FALSE。

##  <a name="autohidepane"></a>CDockingManager::AutoHidePane

创建自动隐藏工具栏。

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>参数

*pBar*<br/>
中指向 "条形图" 窗格的指针。

*pCurrAutoHideToolBar*<br/>
中指向自动隐藏工具栏的指针。

### <a name="return-value"></a>返回值

如果未创建自动隐藏工具栏, 则为 NULL;否则为指向新工具栏的指针。

##  <a name="bringbarstotop"></a>CDockingManager::BringBarsToTop

将具有指定对齐方式的停靠栏引入到顶部。

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>参数

*dwAlignment*<br/>
中停靠到其他窗口顶部的停靠条的对齐方式。

*bExcludeDockedBars*<br/>
中若要使停靠的条不在顶部, 则为 TRUE;否则为 FALSE。

##  <a name="buildpanesmenu"></a>  CDockingManager::BuildPanesMenu

将停靠窗格和工具栏的名称添加到菜单中。

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>参数

*下拉菜单*<br/>
中用于将停靠窗格和工具栏的名称添加到的菜单。

*bToolbarsOnly*<br/>
中如果仅将工具栏名称添加到菜单, 则为 TRUE;否则为 FALSE。

##  <a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect

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

*pWnd*<br/>
中指向要停靠的窗口的指针。

*ptMouse*<br/>
中鼠标位置。

*rectResult*<br/>
弄计算矩形。

*bDrawTab*<br/>
中若要绘制选项卡, 则为 TRUE;否则为 FALSE。

*ppTargetBar*<br/>
弄指向目标窗格的指针的指针。

### <a name="remarks"></a>备注

如果用户将窗口拖动到*ptMouse*指定的点并将其停靠在该处, 此方法将计算窗口将占用的矩形。

##  <a name="create"></a>CDockingManager:: Create

创建扩展管理器。

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
中指向停靠管理器的父帧的指针。 此值不得为 NULL。

### <a name="return-value"></a>返回值

始终为 TRUE。

##  <a name="determinepaneandstatus"></a>CDockingManager::D eterminePaneAndStatus

确定包含给定点及其停靠状态的窗格。

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
中要检查的窗格的位置。

*nSensitivity*<br/>
中要增加每个选中窗格的窗口矩形的值。 如果给定点在此增加的区域中, 则窗格满足搜索条件。

*dwEnabledAlignment*<br/>
中停靠窗格的对齐方式。

*ppTargetBar*<br/>
弄指向目标窗格的指针的指针。

*pBarToIgnore*<br/>
中方法忽略的窗格。

*pBarToDock*<br/>
中停靠的窗格。

### <a name="return-value"></a>返回值

停靠状态。

### <a name="remarks"></a>备注

停靠状态可以是以下值之一:

|AFX_CS_STATUS 值|含义|
|---------------------------|-------------|
|CS_NOTHING|指针不在停靠站点上。 因此, 请使窗格保持浮动。|
|CS_DOCK_IMMEDIATELY|在 "即时" 模式下, 指针位于停靠站点上 (启用了 DT_IMMEDIATE 样式), 因此必须立即停靠该窗格。|
|CS_DELAY_DOCK|指针位于作为另一个停靠窗格或作为主框架边缘的停靠站点上。|
|CS_DELAY_DOCK_TO_TAB|指针位于停靠站点上, 使窗格停靠在选项卡式窗口中。 当鼠标悬停在另一个停靠窗格或选项卡式窗格的选项卡区域上时, 将发生这种情况。|

##  <a name="disablerestoredockstate"></a>CDockingManager::D isableRestoreDockState

启用或禁用从注册表加载停靠布局。

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>参数

*bDisable*<br/>
中若要禁止从注册表加载停靠布局, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果在加载应用程序状态时必须保留停靠窗格和工具栏的当前布局, 请调用此方法。

##  <a name="dockpane"></a>CDockingManager::D ockPane

将一个窗格停靠到另一个窗格或框架窗口。

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

*pBar*<br/>
中指向要停靠到的栏窗格的指针。

*nDockBarID*<br/>
中要停靠的栏的 id。

*lpRect*<br/>
中目标矩形。

##  <a name="dockpaneleftof"></a>  CDockingManager::DockPaneLeftOf

将窗格停靠到另一个窗格的左侧。

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>参数

*pBarToDock*<br/>
中指向要停靠在*pTargetBar*左侧的窗格的指针。

*pTargetBar*<br/>
中指向目标窗格的指针。

### <a name="return-value"></a>返回值

如果窗格已成功停靠, 则为 TRUE;否则为 FALSE。

##  <a name="enableautohidepanes"></a>  CDockingManager::EnableAutoHidePanes

允许将窗格停靠到主框架, 创建停靠窗格, 并将其添加到控件条列表。

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
中停靠对齐方式。

### <a name="return-value"></a>返回值

如果已成功创建停靠窗格, 则为 TRUE;否则为 FALSE。

##  <a name="enabledocking"></a>CDockingManager:: EnableDocking

创建停靠窗格, 并使窗格停靠在主框架中。

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
中停靠对齐方式。

### <a name="return-value"></a>返回值

如果已成功创建停靠窗格, 则为 TRUE;否则为 FALSE。

##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu

显示一个附加按钮, 该按钮打开所有停靠窗格标题上的弹出菜单。

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中若要启用停靠站点菜单, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

"停靠站点" 菜单显示以下用于更改窗格停靠状态的选项:

- `Floating`-浮动窗格

- `Docking`-在主框架中将窗格停靠在窗格的上一次停靠位置

- `AutoHide`-将窗格切换为自动隐藏模式

- `Hide`-隐藏窗格

默认情况下, 不显示此菜单。

##  <a name="enablepanecontextmenu"></a>  CDockingManager::EnablePaneContextMenu

当用户单击鼠标右键并且库正在处理 WM_CONTEXTMENU 消息时, 通知库显示具有应用程序工具栏和停靠窗格列表的特定上下文菜单。

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中如果为 TRUE, 则库启用自动上下文菜单的支持;如果为 FALSE, 则库关闭对自动上下文菜单的支持。

*uiCustomizeCmd*<br/>
中菜单中**自定义**项的命令 id。

*strCustomizeText*<br/>
中**自定义**项的文本。

*bToolbarsOnly*<br/>
中如果为 TRUE, 则菜单只显示应用程序工具栏的列表;如果为 FALSE, 则库将向此列表中添加应用程序停靠窗格。

##  <a name="finddocksite"></a>CDockingManager::FindDockSite

检索位于指定位置并且具有指定对齐方式的栏窗格。

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>参数

*dwAlignment*<br/>
中条形图窗格的对齐方式。

*bOuter*<br/>
中如果为 TRUE, 则检索控件条列表中头位置的条。 否则, 请在控件条列表的尾部位置中检索条。

### <a name="return-value"></a>返回值

具有指定对齐方式的停靠窗格;否则为 NULL。

##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID

按指定的控件 ID 查找窗格。

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>参数

*uBarID*<br/>
中指定要查找的窗格的控件 ID。

*bSearchMiniFrames*<br/>
中若要在搜索中包含所有浮动窗格, 则为 TRUE。 如果仅包含停靠的窗格, 则为 FALSE。

### <a name="return-value"></a>返回值

具有指定控件 ID 的[CBasePane](../../mfc/reference/cbasepane-class.md)对象; 如果找不到指定的窗格, 则为 NULL。

### <a name="remarks"></a>备注

##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane

返回具有目标栏窗格 id 的栏窗格。

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>参数

*pTargetBar*<br/>
中指向目标栏窗格的指针。

### <a name="return-value"></a>返回值

具有目标栏窗格 id 的 "条形图" 窗格;如果不存在这样的栏窗格, 则为 NULL。

##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects

将所有当前工具栏位置提交到虚拟矩形。

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>备注

当用户开始拖动工具栏时, 应用程序会记住其在*虚拟矩形*中的原始位置。 当用户在其停靠网站上移动工具栏时, 该工具栏可能会移动其他工具栏。 其他工具栏的原始位置存储在相应的虚拟矩形中。

##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint

返回包含给定点的帧。

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
中指定要检查的以屏幕坐标表示的点。

*pFrameToExclude*<br/>
中指向要排除的帧的指针。

*bFloatMultiOnly*<br/>
中若要排除不是实例的`CMultiPaneFrameWnd`帧, 则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

包含给定点的帧;否则为 NULL。

##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds

获取包含工作区的边界的矩形。

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>参数

*rcClient*<br/>
弄对包含工作区边界的矩形的引用。

### <a name="return-value"></a>返回值

包含工作区的边界的矩形。

##  <a name="getdockingmode"></a>CDockingManager::GetDockingMode

返回当前停靠模式。

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>返回值

一个表示当前停靠模式的枚举器值。 它可以是下列值之一:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>备注

若要设置停靠模式, 请调用[CDockingManager:: SetDockingMode](#setdockingmode)。

##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd

获取指向父窗口框架的指针。

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>返回值

指向父窗口框架的指针。

##  <a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment

返回已启用的窗格对齐方式。

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>返回值

CBRS_ALIGN_ 标志的按位组合, 如果未启用自动隐藏窗格, 则为0。 有关详细信息, 请参阅[CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking)。

### <a name="remarks"></a>备注

方法为自动隐藏控件条返回启用对齐方式。 若要启用自动隐藏栏, 请调用[CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)。

##  <a name="getminiframes"></a>CDockingManager::GetMiniFrames

获取 miniframes 的列表。

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>返回值

包含属于停靠管理器的控件条的 miniframes 的列表。

##  <a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds

获取一个矩形, 其中包含框架的外边缘。

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>返回值

一个包含帧外边缘的矩形。

##  <a name="getpanelist"></a>CDockingManager::GetPaneList

返回属于停靠管理器的窗格的列表。 这包括所有浮动窗格。

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>参数

*lstBars*<br/>
[in, out]包含当前停靠管理器的所有窗格。

*bIncludeAutohide*<br/>
中如果包含处于自动隐藏模式下的窗格, 则为 TRUE;否则为 FALSE。

*pRTCFilter*<br/>
中如果不为 NULL, 则返回的列表仅包含指定运行时类的窗格。

*bIncludeTabs*<br/>
中如果包含制表符, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果停靠管理器中有任何选项卡式窗格, 该方法将返回指向[CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)对象的指针, 并且必须显式枚举选项卡。

使用*pRTCFilter*获取特定类的窗格。 例如, 您可以通过适当地设置此值来获取工具栏。

##  <a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager

检索指向智能停靠管理器的指针。

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>返回值

指向智能停靠管理器的指针。

##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent

检索指向智能停靠管理器的指针。

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>返回值

指向智能停靠管理器的指针。

##  <a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams

返回停靠管理器的智能停靠参数。

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>返回值

包含当前停靠管理器的智能停靠参数的类。 有关详细信息, 请参阅[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)。

### <a name="remarks"></a>备注

##  <a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes

隐藏处于自动隐藏模式下的窗格。

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>参数

*pBarToExclude*<br/>
中指向要从隐藏中排除的栏的指针。

*bImmediately*<br/>
中若要立即隐藏窗格, 则为 TRUE;若为 FALSE, 则隐藏带有自动隐藏效果的窗格。

##  <a name="insertdocksite"></a>  CDockingManager::InsertDockSite

创建停靠窗格, 并将其插入到控件条列表中。

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>参数

info<br/>
中一个结构, 其中包含有关停靠窗格的对齐信息。

*dwAlignToInsertAfter*<br/>
中停靠窗格的对齐方式。

*ppDockBar*<br/>
弄指向停靠窗格指针的指针。

### <a name="return-value"></a>返回值

如果已成功创建停靠窗格, 则为 TRUE;否则为 FALSE。

##  <a name="insertpane"></a>  CDockingManager::InsertPane

将控件窗格插入到控件条列表中。

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>参数

*pControlBar*<br/>
中指向控件窗格的指针。

*pTarget*<br/>
中指向目标窗格的指针。

*bAfter*<br/>
中若要在目标窗格的位置之后插入窗格, 则为 TRUE; 否则为。否则为 FALSE。

### <a name="return-value"></a>返回值

如果控件窗格成功添加到控件条列表中, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果控件窗格已在控件条列表中, 或者在控件栏列表中不存在目标窗格, 则此方法返回 false。

##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu

指定是否在所有窗格的标题上显示弹出菜单。

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>返回值

如果 "停靠网站" 菜单显示在所有停靠窗格的标题上, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

可以通过调用[CDockingManager:: EnableDockSiteMenu](#enabledocksitemenu)启用停靠站点菜单。

##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout

确定是否调整所有窗格的布局。

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>返回值

如果调整所有窗格的布局, 则为 TRUE;否则为 FALSE。

##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode

指定停靠管理器是否处于 OLE 容器模式。

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>返回值

如果停靠管理器处于 OLE 容器模式, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在 OLE 容器模式下, 隐藏所有停靠窗格和应用程序工具栏。 如果将[CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)设置为 TRUE, 则此模式下的窗格也将隐藏。

##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite

确定指定点是否在停靠站点附近。

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>参数

*point*<br/>
中指定的点。

*dwBarAlignment*<br/>
弄指定点附近的边缘。 可能的值包括 CBRS_ALIGN_LEFT、CBRS_ALIGN_RIGHT、CBRS_ALIGN_TOP 和 CBRS_ALIGN_BOTTOM。

*bOuterEdge*<br/>
弄如果点位于停靠站点的外边框附近, 则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

如果点在停靠站点附近, 则为 TRUE;否则为 FALSE。

##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid

确定是否设置了 "打印预览" 模式。

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>返回值

如果设置了打印预览模式, 则为 TRUE;否则为 FALSE。

##  <a name="loadstate"></a>  CDockingManager::LoadState

从注册表加载停靠管理器的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中配置文件名称。

*uiID*<br/>
中停靠管理器的 id。

### <a name="return-value"></a>返回值

如果已成功加载插接管理器状态, 则为 TRUE;否则为 FALSE。

##  <a name="lockupdate"></a>CDockingManager::LockUpdate

锁定给定的窗口。

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>参数

*bLock*<br/>
中如果窗口被锁定, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

当窗口处于锁定状态时, 它无法移动, 因此不能进行重绘。

##  <a name="m_bhidedockingbarsincontainermode"></a>  CDockingManager::m_bHideDockingBarsInContainerMode

指定停靠管理器是否在 OLE 容器模式下隐藏窗格。

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>备注

如果希望在应用程序处于 OLE 容器模式时将所有窗格都停靠到主框架, 请将此值设置为 "FALSE"。 默认情况下, 此值为 TRUE。

##  <a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal

指定全局停靠模式。

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>备注

默认情况下, 每个停靠窗格都使用此停靠模式。 有关此字段可以设置到的值的详细信息, 请参阅[CBasePane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)。

##  <a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity

指定停靠敏感度。

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>备注

停靠敏感度定义了在框架将其状态更改为停靠之前, 浮动窗格可以如何接近停靠窗格、停靠站点或其他窗格。

##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock

指定停靠窗格在直接停靠模式下停靠之前的时间 (以毫秒为单位)。

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>备注

停靠窗格之前, 框架将等待指定的时间长度。 这可防止在用户仍拖动时不会将窗格意外停靠到某个位置。

##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock

指定工具栏停靠在主框架窗口之前的时间 (以毫秒为单位)。

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>备注

停靠工具栏之前, 框架将等待指定的时间长度。 这可以防止在用户仍拖动时, 将工具栏意外停靠到某个位置。

##  <a name="onactivateframe"></a>CDockingManager::OnActivateFrame

当框架窗口被激活或停用时由框架调用。

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>参数

*bActivate*<br/>
中如果为 TRUE, 则使框架窗口处于活动状态;如果为 FALSE, 则停用框架窗口。

##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu

当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>备注

框架将在即将关闭当前主窗口时发送 WM_DESTROY 消息。 当对象处理 WM_DESTROY 消息时, `CMFCPopupMenu`重写此方法以处理属于框架窗口的对象中的通知。 `CMFCPopupMenu`

##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame

由框架调用以移动微型框架窗口。

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>参数

*pFrame*<br/>
中指向袖珍框架窗口的指针。

### <a name="return-value"></a>返回值

如果该方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu

当框架生成包含窗格列表的菜单时由框架调用。

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>参数

*point*<br/>
中指定菜单的位置。

##  <a name="panefrompoint"></a>CDockingManager::P aneFromPoint

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

*point*<br/>
中指定要检查的以屏幕坐标表示的点。

*nSensitivity*<br/>
中用于使每个选中窗格的窗口矩形的值。 如果给定点在此放大区域中, 则窗格满足搜索条件。

*bExactBar*<br/>
中若要忽略*nSensitivity*参数, 则为 TRUE;否则为 FALSE。

*pRTCBarType*<br/>
中如果不为 NULL, 则方法只搜索指定类型的窗格。

*bCheckVisibility*<br/>
中如果仅检查可见窗格, 则为 TRUE;否则为 FALSE。

*dwAlignment*<br/>
弄如果在指定的点找到了窗格, 则此参数包含与指定点最近的窗格的一侧。 有关详细信息，请参阅“备注”部分。

*pBarToIgnore*<br/>
中如果不为 NULL, 则该方法将忽略此参数指定的窗格。

### <a name="return-value"></a>返回值

包含给定点的[CBasePane](../../mfc/reference/cbasepane-class.md)派生对象, 如果未找到任何窗格, 则为 NULL。

### <a name="remarks"></a>备注

当函数返回并找到一个窗格时, *dwAlignment*包含指定点的对齐方式。 例如, 如果该点离窗格顶部最近, 则*dwAlignment*设置为 CBRS_ALIGN_TOP。

##  <a name="processpanecontextmenucommand"></a>  CDockingManager::ProcessPaneContextMenuCommand

由框架调用以选择或清除指定命令的复选框, 并重新计算显示的窗格的布局。

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>参数

*nID*<br/>
中菜单中的控件条的 id。

*nCode*<br/>
中命令通知代码。

*pExtra*<br/>
中指向 void 的指针, `CCmdUI`如果*nCode*为 CN_UPDATE_COMMAND_UI, 则为指向强制转换的指针。

*pHandlerInfo*<br/>
中指向信息结构的指针。 未使用此参数。

### <a name="return-value"></a>返回值

如果*pEXtra*不为 NULL 且*nCode*等于 CN_UPDATE_COMMAND_UI, 则为 TRUE; 否则为。

##  <a name="recalclayout"></a>  CDockingManager::RecalcLayout

重新计算控件列表中存在的控件的内部布局。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

*bNotify*<br/>
中未使用此参数。

##  <a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers

释放空窗格容器。

```
void ReleaseEmptyPaneContainers();
```

##  <a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar

删除指定的隐藏栏窗格。

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>参数

*pBar*<br/>
中指向要删除的栏窗格的指针。

##  <a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame

从微型帧列表中删除指定的帧。

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向要删除的帧的指针。

### <a name="return-value"></a>返回值

如果删除指定的帧, 则为 TRUE;否则为 FALSE。

##  <a name="removepanefromdockmanager"></a>  CDockingManager::RemovePaneFromDockManager

取消注册窗格, 并将其从停靠管理器的列表中删除。

```
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向要删除的窗格的指针。

*bDestroy*<br/>
中如果为 TRUE, 则删除的窗格被销毁。

*bAdjustLayout*<br/>
中如果为 TRUE, 则立即调整停靠布局。

*bAutoHide*<br/>
中如果为 TRUE, 则从自动隐藏栏列表中删除该窗格。 如果为 FALSE, 则从常规窗格列表中删除该窗格。

*pBarReplacement*<br/>
中指向替换已删除窗格的窗格的指针。

##  <a name="replacepane"></a>CDockingManager::ReplacePane

用一个窗格替换另一个窗格。

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>参数

*pOriginalBar*<br/>
中指向原始窗格的指针。

*pNewBar*<br/>
中指向替换原始窗格的窗格的指针。

### <a name="return-value"></a>返回值

如果成功替换窗格, 则为 TRUE;否则为 FALSE。

##  <a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder

在小型帧列表中滑雪场帧。

```
void ResortMiniFramesForZOrder();
```

##  <a name="savestate"></a>CDockingManager:: SaveState

将停靠管理器的状态保存到注册表中。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中注册表项的路径。

*uiID*<br/>
中停靠管理器 ID。

### <a name="return-value"></a>返回值

如果成功保存状态, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

将停靠管理器的状态保存到注册表中涉及到保存控制条状态、自动隐藏栏的状态, 以及停靠管理器中存在的迷你帧的状态。

##  <a name="sendmessagetominiframes"></a>  CDockingManager::SendMessageToMiniFrames

向所有微型帧发送指定的消息。

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>参数

*uMessage*<br/>
中要发送的消息。

*wParam*<br/>
中其他消息相关的信息。

*lParam*<br/>
中其他消息相关的信息。

### <a name="return-value"></a>返回值

始终为 TRUE。

##  <a name="serialize"></a>CDockingManager:: 串行化

将扩展管理器写入存档。

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
中对存档对象的引用。

### <a name="remarks"></a>备注

将停靠管理器写入存档涉及确定停靠控制条和滑块的数目, 并将控制条、微型帧、自动隐藏栏和 MDI 选项卡式条写入存档。

##  <a name="setautohidezorder"></a>  CDockingManager::SetAutohideZOrder

设置控件条和指定窗格的大小、宽度和高度。

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>参数

*pAHDockingBar*<br/>
中指向可停靠的窗格的指针。

##  <a name="setdockingmode"></a>  CDockingManager::SetDockingMode

设置停靠模式。

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>参数

*dockMode*<br/>
指定新的停靠模式。 有关详细信息，请参阅“备注”部分。

*主体*<br/>
指定要用于智能停靠标记的主题。 它可以是下列枚举值之一:AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>备注

调用此静态方法以设置停靠模式。

*dockMode*可以是下列值之一:

- DT_STANDARD-标准停靠模式, 在 Visual Studio .NET 2003 中实现。 不通过拖动上下文拖动窗格。

- DT_IMMEDIATE-在 Microsoft Visio 中实现的即时停靠模式。 用拖动上下文拖动窗格, 但不显示标记。

- DT_SMART-在 Visual Studio 2005 中实现的智能停靠模式。 通过拖动上下文拖动窗格, 并显示显示窗格可停靠位置的智能标记。

##  <a name="setdockstate"></a>  CDockingManager::SetDockState

设置控制条、微型帧和自动隐藏栏的停靠状态。

```
virtual void SetDockState();
```

##  <a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode

设置打印预览中显示的条形的打印预览模式。

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>参数

*bPreview*<br/>
中如果设置了打印预览模式, 则为 TRUE;否则为 FALSE。

*pState*<br/>
中指向预览状态的指针。 未使用此参数。

##  <a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams

设置用于定义智能停靠行为的参数。

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>参数

*params*<br/>
[in, out]定义智能停靠的参数。

### <a name="remarks"></a>备注

如果要自定义智能停靠标记的外观、颜色或形状, 请调用此方法。

若要使用默认查找智能停靠标记, 请将未初始化的[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)的实例传递给*params*。

##  <a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames

显示或隐藏微型框架的窗口。

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
中若要使所显示的帧的窗口处于活动状态, 则为 TRUE;若为 FALSE, 则隐藏框架的窗口。

##  <a name="showpanes"></a>CDockingManager::ShowPanes

显示或隐藏控件窗格和自动隐藏栏。

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
中如果显示窗格, 则为 TRUE;如果隐藏窗格, 则为 FALSE。

### <a name="return-value"></a>返回值

始终为 FALSE。

##  <a name="startsdocking"></a>CDockingManager::StartSDocking

根据智能停靠管理器的对齐方式, 启动指定窗口的智能停靠。

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>参数

*pDockingWnd*<br/>
中指向停靠窗口的指针。

##  <a name="stopsdocking"></a>CDockingManager::StopSDocking

停止智能停靠。

```
void StopSDocking();
```

##  <a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme

返回用于显示智能停靠标记的主题的静态方法。

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>返回值

返回以下枚举值之一:AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)
