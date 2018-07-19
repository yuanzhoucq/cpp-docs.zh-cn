---
title: CDockingManager 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87fcaf93823e504f3631d50de4f981ae30e882e9
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027821"
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
|[CDockingManager::AddDockSite](#adddocksite)|创建一个停靠窗格并将其添加到控件条的列表。|  
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|将句柄添加到一个栏窗格的隐藏 MDI 选项卡式窗格栏列表。|  
|[CDockingManager::AddMiniFrame](#addminiframe)|将帧添加到微型框架的列表。|  
|[CDockingManager::AddPane](#addpane)|注册到停靠管理器窗格。|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|重新计算并调整布局的框架窗口中的所有窗格。|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|使 WM_NCCALCSIZE 消息要发送到所有窗格和`CPaneFrameWnd`windows。|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|调整矩形的对齐方式。|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|调整自动隐藏模式中的停靠窗格的大小，以便它采用全角或括在框架的工作区的高度停靠站点。|  
|[CDockingManager::AutoHidePane](#autohidepane)|创建自动隐藏工具栏。|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|将具有指定的对齐方式到顶部的停靠的栏。|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|将停靠窗格和工具栏的名称添加到菜单。|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|计算停靠窗口的预期的矩形。|  
|[CDockingManager::Create](#create)|创建停靠管理器。|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|确定包含给定的点和其停靠状态的窗格。|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|启用或禁用的停靠布局从注册表加载。|  
|[CDockingManager::DockPane](#dockpane)|将窗格停靠到另一个窗格或框架窗口。|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|将窗格停靠到另一个窗格的左侧。|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|使窗格的停靠到主框架，创建一个停靠窗格中，并将其添加到控件条的列表。|  
|[CDockingManager::EnableDocking](#enabledocking)|创建将停靠窗格并启用窗格的停靠到主框架。|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|显示一个额外的按钮打开一个弹出菜单上的所有停靠的窗格的标题。|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|通知库以显示具有应用程序工具栏和停靠窗格的列表，用户单击鼠标右键按钮和库处理 WM_CONTEXTMENU 消息时的特殊上下文菜单。|  
|[CDockingManager::FindDockSite](#finddocksite)|检索在栏窗格的位于指定位置并具有指定的对齐方式。|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|返回在栏窗格具有目标状态栏窗格的 id。|  
|[CDockingManager::FindPaneByID](#findpanebyid)|查找窗格由指定的控件 id。|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|提交到虚拟矩形的所有当前工具栏位置。|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|返回包含给定的点的帧。|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|获取包含客户端区域的边界的矩形。|  
|[CDockingManager::GetDockingMode](#getdockingmode)|返回当前的停靠模式。|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|获取一个指针指向父窗口框架。|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|返回窗格的已启用对齐方式。|  
|[CDockingManager::GetMiniFrames](#getminiframes)|获取小型机的列表。|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|获取包含在帧的外边缘的矩形。|  
|[CDockingManager::GetPaneList](#getpanelist)|返回属于到停靠管理器窗格的列表。 这包括所有浮动窗格。|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|检索指向智能停靠管理器。|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|检索指向智能停靠管理器。|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|返回到停靠管理器的智能停靠参数。|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|返回一个用来显示智能停靠标记的主题的静态方法。|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|隐藏窗格，只是在自动隐藏模式下。|  
|[CDockingManager::InsertDockSite](#insertdocksite)|创建将停靠窗格并将其插入到控件条的列表。|  
|[CDockingManager::InsertPane](#insertpane)|将控制窗格插入到控件条的列表。|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|指定是否在所有窗格的标题上显示一个弹出菜单。|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|确定是否调整所有窗格的布局。|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|指定到停靠管理器是否在 OLE 容器模式下。|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|确定指定的点是否在停靠站点附近。|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|确定是否设置打印预览模式。|  
|[CDockingManager::LoadState](#loadstate)|从注册表加载到停靠管理器的状态。|  
|[CDockingManager::LockUpdate](#lockupdate)|将锁定给定的窗口。|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|框架窗口使处于活动状态或停用时由框架调用。|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|由框架调用以移动微型框架窗口。|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|生成具有一组窗格菜单时由框架调用。|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|返回包含给定的点的窗格。|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|由框架调用以选择或以清除复选框为指定的命令并重新计算显示窗格的布局。|  
|[CDockingManager::RecalcLayout](#recalclayout)|重新计算的控件列表中存在的控件的内部布局。|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|释放空窗格容器。|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|移除指定的隐藏栏窗格。|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|从微型框架的列表中删除指定的范围。|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|注销一个窗格，并将其从列表中到停靠管理器删除。|  
|[CDockingManager::ReplacePane](#replacepane)|用一个窗格替换另一个窗格。|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|较微型框架的列表中的框架。|  
|[CDockingManager::SaveState](#savestate)|将停靠管理器的状态保存到注册表。|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|将指定的消息发送到所有微型框架。|  
|[CDockingManager::Serialize](#serialize)|写入存档到停靠管理器。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|设置大小、 宽度和高度的控件条和指定的窗格。|  
|[CDockingManager::SetDockingMode](#setdockingmode)|设置停靠模式。|  
|[CDockingManager::SetDockState](#setdockstate)|设置停靠控件条、 最小的帧中，和自动隐藏栏的状态。|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|设置的条形图的打印预览中显示打印预览模式。|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|设置用于定义智能停靠的行为的参数。|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|显示或隐藏的微型框架窗口。|  
|[CDockingManager::ShowPanes](#showpanes)|显示或隐藏的控件和自动隐藏栏的窗格。|  
|[CDockingManager::StartSDocking](#startsdocking)|启动智能停靠的智能停靠管理器的对齐方式根据指定的窗口。|  
|[CDockingManager::StopSDocking](#stopsdocking)|停止智能停靠。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|指定是否停靠管理器将隐藏在 OLE 容器模式下的窗格。|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|指定的全局停靠模式。|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|指定停靠的敏感度。|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|指定以毫秒为单位之前停靠窗格停靠在立即停靠模式下, 的时间。|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|指定以毫秒为单位之前工具栏停靠到主框架窗口, 的时间。|  
  
## <a name="remarks"></a>备注  
 主框架窗口创建并自动初始化此类。  
  
 停靠管理器对象持有的所有窗格中的停靠布局的列表以及所有的列表[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)属于主框架窗口的 windows。  
  
 `CDockingManager`类实现可用于查找一个窗格，某些服务或`CPaneFrameWnd`窗口。 通常不调用这些服务直接因为包装在主框架窗口对象。 有关详细信息，请参阅[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)。  
  
## <a name="customization-tips"></a>自定义提示  
 以下提示适用于`CDockingManager`对象：  
  
- [CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)支持这些停靠模式：  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     由定义这些停靠模式[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)并通过调用设置[CDockingManager::SetDockingMode](#setdockingmode)。  
  
-   如果你想要创建非浮动、 无法调整大小的窗格中，调用[CDockingManager::AddPane](#addpane)方法。 此方法注册到停靠管理器，它负责窗格的布局窗格。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用中的各种方法`CDockingManager`类，以配置`CDockingManager`对象。 该示例演示如何显示一个额外的按钮将打开一个弹出菜单上的所有停靠的窗格的标题，以及如何设置该对象的停靠模式。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxDockingManager.h  
  
##  <a name="adddocksite"></a>  CDockingManager::AddDockSite  
 创建一个停靠窗格并将其添加到控件条的列表。  
  
```  
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*信息*  
 对包含的信息结构的引用将停靠窗格对齐方式。  
  
 [out]*ppDockBar*  
 指向到新的停靠窗格的指针的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建停靠窗格，则返回 TRUEFALSE 否则为。  
  
##  <a name="addhiddenmditabbedbar"></a>  CDockingManager::AddHiddenMDITabbedBar  
 将句柄添加到一个栏窗格的隐藏 MDI 选项卡式窗格栏列表。  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBar*  
 指向一个栏窗格  
  
##  <a name="addpane"></a>  CDockingManager::AddPane  
 注册到停靠管理器窗格。  
  
```  
BOOL AddPane(
    CBasePane* pWnd,  
    BOOL bTail = TRUE,  
    BOOL bAutoHide = FALSE,  
    BOOL bInsertForOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in、 out]*pWnd*  
 指定要添加到停靠管理器窗格。  
  
 [in]*bTail*  
 为 TRUE，则将窗格添加到窗格的列表的末尾，停靠管理器;否则为 FALSE。  
  
 [in]*bAutoHide*  
 仅限内部使用。 始终使用默认值 FALSE。  
  
 [in]*bInsertForOuterEdge*  
 仅限内部使用。 始终使用默认值 FALSE。  
  
### <a name="return-value"></a>返回值  
 如果窗格已成功注册到停靠管理器; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用此方法，将注册到停靠管理器的非浮动、 无法调整大小的窗格。 如果您执行操作时不会注册窗格中，不会正确显示到停靠管理器的布局方式。  
  
##  <a name="adjustdockinglayout"></a>  CDockingManager::AdjustDockingLayout  
 重新计算并调整布局的框架窗口中的所有窗格。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*hdwp*  
 指定延迟的窗口位置结构。 有关详细信息，请参阅 [Windows 数据类型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="addminiframe"></a>  CDockingManager::AddMiniFrame  
 将帧添加到微型框架的列表。  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in]*pWnd*  
 指向一个帧的指针。  
  
### <a name="return-value"></a>返回值  
 如果帧不是在微型框架的列表中且已添加成功，则为 TRUEFALSE 否则为。  
  
##  <a name="adjustpaneframes"></a>  CDockingManager::AdjustPaneFrames  
 使 WM_NCCALCSIZE 消息要发送到所有窗格和`CPaneFrameWnd`windows。  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="adjustrecttoclientarea"></a>  CDockingManager::AdjustRectToClientArea  
 调整矩形的对齐方式。  
  
```  
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in]*rectResult*  
 对引用`CRect`对象  
  
 [in]*dwAlignment*  
 对齐方式`CRect`对象  
  
### <a name="return-value"></a>返回值  
 则为 TRUE 的对齐方式`CRect`对象进行调整。FALSE 否则为。  
  
### <a name="remarks"></a>备注  
 *DwAlignment*参数可以具有下列值之一：  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="alignautohidepane"></a>  CDockingManager::AlignAutoHidePane  
 调整自动隐藏模式中的停靠窗格的大小，以便它采用全角或括在框架的工作区的高度停靠站点。  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDefaultSlider*  
 滑块的停靠窗格。  
  
 [in]*bIsVisible*  
 如果停靠窗格可见，则为 TRUEFALSE 否则为。  
  
##  <a name="autohidepane"></a>  CDockingManager::AutoHidePane  
 创建自动隐藏工具栏。  
  
```  
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,  
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBar*  
 指向栏的窗格。  
  
 [in]*pCurrAutoHideToolBar*  
 一个指向自动隐藏工具栏。  
  
### <a name="return-value"></a>返回值  
 如果未创建自动隐藏工具栏; 则为 NULL否则为指向新的工具栏。  
  
##  <a name="bringbarstotop"></a>  CDockingManager::BringBarsToTop  
 将具有指定的对齐方式到顶部的停靠的栏。  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*dwAlignment*  
 转到其他窗口顶部的停靠栏的对齐方式。  
  
 [in]*bExcludeDockedBars*  
 为 TRUE，则从顶部; 要排除的停靠的栏否则为 FALSE。  
  
##  <a name="buildpanesmenu"></a>  CDockingManager::BuildPanesMenu  
 将停靠窗格和工具栏的名称添加到菜单。  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>参数  
 [in]*菜单*  
 要添加的停靠窗格和工具栏和名称的菜单。  
  
 [in]*bToolbarsOnly*  
 为 TRUE，则将仅工具栏名称添加到菜单;FALSE 否则为。  
  
##  <a name="calcexpecteddockedrect"></a>  CDockingManager::CalcExpectedDockedRect  
 计算停靠窗口的预期的矩形。  
  
```  
void CalcExpectedDockedRect(
    CWnd* pWnd,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pWnd*  
 指向窗口停靠的指针。  
  
 [in]*ptMouse*  
 鼠标位置。  
  
 [out]*rectResult*  
 计算的矩形。  
  
 [in]*bDrawTab*  
 为 true，则选项卡; 绘图否则为 FALSE。  
  
 [out]*ppTargetBar*  
 指向目标窗格的指针指向的指针。  
  
### <a name="remarks"></a>备注  
 此方法计算一个窗口，如果用户将窗口拖到由指定的点会占用的矩形*ptMouse*和那里停靠。  
  
##  <a name="create"></a>  CDockingManager::Create  
 创建停靠管理器。  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>参数  
 [in]*pParentWnd*  
 指向到停靠管理器与父框架的指针。 此值不能为 NULL。  
  
### <a name="return-value"></a>返回值  
 始终为 TRUE。  
  
##  <a name="determinepaneandstatus"></a>  CDockingManager::DeterminePaneAndStatus  
 确定包含给定的点和其停靠状态的窗格。  
  
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
 [in]*pt*  
 要检查的窗格的位置。  
  
 [in]*nSensitivity*  
 要增加每个选中的窗格的窗口矩形的值。 如果给的定点位于此增加的区域，一个窗格，满足搜索条件。  
  
 [in]*dwEnabledAlignment*  
 停靠的窗格的对齐方式。  
  
 [out]*ppTargetBar*  
 指向目标窗格的指针指向的指针。  
  
 [in]*pBarToIgnore*  
 该方法忽略窗格。  
  
 [in]*pBarToDock*  
 停靠窗格。  
  
### <a name="return-value"></a>返回值  
 停靠状态。  
  
### <a name="remarks"></a>备注  
 停靠状态可以是下列值之一：  
  
|AFX_CS_STATUS 值|含义|  
|---------------------------|-------------|  
|CS_NOTHING|指针不是停靠站点段。 因此，保持窗格处于浮动。|  
|CS_DOCK_IMMEDIATELY|在指针位于转移停靠站点中即时模式 （DT_IMMEDIATE 样式已启用），因此必须立即停靠窗格。|  
|CS_DELAY_DOCK|在指针位于停靠站点是另一个停靠窗格或主框架的一个边缘上。|  
|CS_DELAY_DOCK_TO_TAB|通过使窗格停靠在选项卡式窗口停靠站点是指针。 鼠标位于通过另一个停靠窗格的标题或选项卡式窗格的选项卡区域时，将发生这种情况。|  
  
##  <a name="disablerestoredockstate"></a>  CDockingManager::DisableRestoreDockState  
 启用或禁用的停靠布局从注册表加载。  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bDisable*  
 为 true，则禁用加载的注册表中; 从停靠布局否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 当加载应用程序状态时，必须保留当前布局的停靠窗格和工具栏时调用此方法。  
  
##  <a name="dockpane"></a>  CDockingManager::DockPane  
 将窗格停靠到另一个窗格或框架窗口。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBar*  
 指向一个栏的停靠的窗格。  
  
 [in]*nDockBarID*  
 栏，停靠的 id。  
  
 [in]*lpRect*  
 目标矩形。  
  
##  <a name="dockpaneleftof"></a>  CDockingManager::DockPaneLeftOf  
 将窗格停靠到另一个窗格的左侧。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBarToDock*  
 为停靠到的左窗格中的指针*pTargetBar*。  
  
 [in]*pTargetBar*  
 指向目标窗格的指针。  
  
### <a name="return-value"></a>返回值  
 如果已成功，则停靠窗格，则返回 TRUE否则为 FALSE。  
  
##  <a name="enableautohidepanes"></a>  CDockingManager::EnableAutoHidePanes  
 使窗格的停靠到主框架，创建一个停靠窗格中，并将其添加到控件条的列表。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 [in]*dwStyle*  
 停靠的对齐方式。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建停靠窗格，则返回 TRUEFALSE 否则为。  
  
##  <a name="enabledocking"></a>  CDockingManager::EnableDocking  
 创建将停靠窗格并启用窗格的停靠到主框架。  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 [in]*dwStyle*  
 停靠的对齐方式。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建停靠窗格，则返回 TRUEFALSE 否则为。  
  
##  <a name="enabledocksitemenu"></a>  CDockingManager::EnableDockSiteMenu  
 显示一个额外的按钮打开一个弹出菜单上的所有停靠的窗格的标题。  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bEnable*  
 为 true 以启用停靠站点菜单;否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 停靠站点菜单显示更改窗格的停靠状态的以下选项：  
  
- `Floating` -中时浮动窗格  
  
- `Docking` -将停靠在主窗格中的最后一次停靠位置的位置框架窗格  
  
- `AutoHide` -将窗格切换为自动隐藏模式  
  
- `Hide` -隐藏窗格  
  
 默认情况下，不显示此菜单。  
  
##  <a name="enablepanecontextmenu"></a>  CDockingManager::EnablePaneContextMenu  
 通知库以显示具有应用程序工具栏和停靠窗格的列表，用户单击鼠标右键按钮和库处理 WM_CONTEXTMENU 消息时的特殊上下文菜单。  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bEnable*  
 如果为 TRUE，开启自动进行上下文菜单; 支持库如果为 FALSE 库会关闭自动上下文菜单的支持。  
  
 [in]*uiCustomizeCmd*  
 命令 id**自定义**菜单中的项。  
  
 [in]*strCustomizeText*  
 文本**自定义**项。  
  
 [in]*bToolbarsOnly*  
 如果为 TRUE，菜单会显示列表的应用程序工具栏;如果为 FALSE，库将添加到此列表的应用程序的停靠窗格。  
  
##  <a name="finddocksite"></a>  CDockingManager::FindDockSite  
 检索在栏窗格的位于指定位置并具有指定的对齐方式。  
  
```  
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,  
    BOOL bOuter);
```  
  
### <a name="parameters"></a>参数  
 [in]*dwAlignment*  
 条的对齐方式窗格。  
  
 [in]*bOuter*  
 如果为 TRUE，检索的栏中的控件条列表中的头位置。 否则，检索列表中的控件条的结尾位置中的栏。  
  
### <a name="return-value"></a>返回值  
 具有指定的对齐方式; 停靠窗格否则为 NULL。  
  
##  <a name="findpanebyid"></a>  CDockingManager::FindPaneByID  
 查找窗格由指定的控件 id。  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*uBarID*  
 指定要查找窗格的控件 ID。  
  
 [in]*bSearchMiniFrames*  
 若要在搜索中包括所有在浮动窗格，则为 TRUE。 为 FALSE，则包括仅停靠的窗格。  
  
### <a name="return-value"></a>返回值  
 [CBasePane](../../mfc/reference/cbasepane-class.md)具有指定的控件 ID，则为 NULL，如果找不到指定的窗格中的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="finddocksitebypane"></a>  CDockingManager::FindDockSiteByPane  
 返回在栏窗格具有目标状态栏窗格的 id。  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pTargetBar*  
 指向目标状态栏窗格的指针。  
  
### <a name="return-value"></a>返回值  
 栏 id 为目标栏窗格; 的窗格如果没有此类栏窗格中存在，则为 NULL。  
  
##  <a name="fixupvirtualrects"></a>  CDockingManager::FixupVirtualRects  
 提交到虚拟矩形的所有当前工具栏位置。  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>备注  
 当用户开始拖动一个工具栏时，该应用程序会在其原始位置记住*虚拟矩形*。 当用户在其停靠站点之间移动工具栏时，工具栏可能会发生移动其他工具栏。 其他工具栏的原始位置存储在相应的虚拟矩形中。  
  
##  <a name="framefrompoint"></a>  CDockingManager::FrameFromPoint  
 返回包含给定的点的帧。  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>参数  
 [in]*pt*  
 指定以屏幕坐标，以检查点。  
  
 [in]*pFrameToExclude*  
 指向要排除的帧的指针。  
  
 [in]*bFloatMultiOnly*  
 为 true，则不是实例的排除帧`CMultiPaneFrameWnd`;FALSE 否则为。  
  
### <a name="return-value"></a>返回值  
 包含给定的点; 的框架。否则为 NULL。  
  
##  <a name="getclientareabounds"></a>  CDockingManager::GetClientAreaBounds  
 获取包含客户端区域的边界的矩形。  
  
```  
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```  
  
### <a name="parameters"></a>参数  
 [out]*rcClient*  
 对包含客户端区域的边界的矩形的引用。  
  
### <a name="return-value"></a>返回值  
 包含客户端区域的边界的矩形。  
  
##  <a name="getdockingmode"></a>  CDockingManager::GetDockingMode  
 返回当前的停靠模式。  
  
```  
static AFX_DOCK_TYPE GetDockingMode();
```  
  
### <a name="return-value"></a>返回值  
 一个枚举器值，表示当前停靠模式。 它可以是下列值之一：  
  
- DT_STANDARD  
  
- DT_IMMEDIATE  
  
- DT_SMART  
  
### <a name="remarks"></a>备注  
 若要设置停靠模式，请调用[CDockingManager::SetDockingMode](#setdockingmode)。  
  
##  <a name="getdocksiteframewnd"></a>  CDockingManager::GetDockSiteFrameWnd  
 获取一个指针指向父窗口框架。  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向父窗口框架的指针。  
  
##  <a name="getenabledautohidealignment"></a>  CDockingManager::GetEnabledAutoHideAlignment  
 返回窗格的已启用对齐方式。  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>返回值  
 CBRS_ALIGN_ 标志或如果未启用自动隐藏窗格，则为 0 的按位组合。 有关详细信息，请参阅[CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking)。  
  
### <a name="remarks"></a>备注  
 该方法返回的已启用自动隐藏控件条对齐方式。 若要启用自动隐藏栏，请调用[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)。  
  
##  <a name="getminiframes"></a>  CDockingManager::GetMiniFrames  
 获取小型机的列表。  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含属于到停靠管理器的控件条的小型机的列表。  
  
##  <a name="getouteredgebounds"></a>  CDockingManager::GetOuterEdgeBounds  
 获取包含在帧的外边缘的矩形。  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含框架的外边缘的矩形。  
  
##  <a name="getpanelist"></a>  CDockingManager::GetPaneList  
 返回属于到停靠管理器窗格的列表。 这包括所有浮动窗格。  
  
```  
void GetPaneList(
    CObList& lstBars,  
    BOOL bIncludeAutohide = FALSE,  
    CRuntimeClass* pRTCFilter = NULL,  
    BOOL bIncludeTabs = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in、 out]*lstBars*  
 包含当前停靠管理器的所有窗格。  
  
 [in]*bIncludeAutohide*  
 为 TRUE，则包括处于自动隐藏模式; 窗格否则为 FALSE。  
  
 [in]*pRTCFilter*  
 如果不为 NULL，返回的列表将包含仅指定的运行时类的窗格。  
  
 [in]*bIncludeTabs*  
 为 TRUE，则包括选项卡;否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 如果到停靠管理器中不存在任何选项卡式的窗格，该方法返回指向[CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)对象，并且您必须显式枚举选项卡。  
  
 使用*pRTCFilter*若要获取特定类别的窗格。 例如，您可以通过适当地设置此值获取仅工具栏。  
  
##  <a name="getsmartdockingmanager"></a>  CDockingManager::GetSmartDockingManager  
 检索指向智能停靠管理器。  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>返回值  
 一个指向[智能停靠管理器](http://msdn.microsoft.com/f537a1a6-fb9e-41d7-952f-0f25d5ee7534)。  
  
##  <a name="getsmartdockingmanagerpermanent"></a>  CDockingManager::GetSmartDockingManagerPermanent  
 检索指向智能停靠管理器。  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>返回值  
 智能停靠管理器指向的指针。  
  
##  <a name="getsmartdockingparams"></a>  CDockingManager::GetSmartDockingParams  
 返回到停靠管理器的智能停靠参数。  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>返回值  
 有关当前停靠管理器包含智能停靠参数的类。 有关详细信息，请参阅[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hideautohidepanes"></a>  CDockingManager::HideAutoHidePanes  
 隐藏窗格，只是在自动隐藏模式下。  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBarToExclude*  
 指向要排除隐藏的条的指针。  
  
 [in]*bImmediately*  
 为 TRUE，则立即; 隐藏窗格为 FALSE，则隐藏自动隐藏效果窗格。  
  
##  <a name="insertdocksite"></a>  CDockingManager::InsertDockSite  
 创建将停靠窗格并将其插入到控件条的列表。  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*信息*  
 包含有关停靠窗格中的对齐方式信息的结构。  
  
 [in]*dwAlignToInsertAfter*  
 停靠窗格的对齐方式。  
  
 [out]*ppDockBar*  
 指向将停靠窗格的指针指向的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建停靠窗格，则返回 TRUEFALSE 否则为。  
  
##  <a name="insertpane"></a>  CDockingManager::InsertPane  
 将控制窗格插入到控件条的列表。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*pControlBar*  
 指向控制窗格的指针。  
  
 [in]*pTarget*  
 指向目标窗格的指针。  
  
 [in]*bAfter*  
 为 TRUE，则目标窗格中; 位置之后插入窗格FALSE 否则为。  
  
### <a name="return-value"></a>返回值  
 如果控件窗格中已成功添加到列表控件条; 则为 TRUEFALSE 否则为。  
  
### <a name="remarks"></a>备注  
 控件窗格中是否已在列表中的控件条或控件条列表中不存在目标窗格中，此方法返回 false。  
  
##  <a name="isdocksitemenu"></a>  CDockingManager::IsDockSiteMenu  
 指定是否在所有窗格的标题上显示一个弹出菜单。  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>返回值  
 如果停靠站点菜单显示在标题的所有停靠窗格; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 可以通过调用启用停靠站点菜单[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)。  
  
##  <a name="isinadjustlayout"></a>  CDockingManager::IsInAdjustLayout  
 确定是否调整所有窗格的布局。  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果所有窗格的布局调整，则为 TRUEFALSE 否则为。  
  
##  <a name="isolecontainermode"></a>  CDockingManager::IsOLEContainerMode  
 指定到停靠管理器是否在 OLE 容器模式下。  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果到停靠管理器中 OLE 容器模式，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 在 OLE 容器模式下，隐藏所有停靠窗格和应用程序工具栏。 如果设置了窗格也会隐藏在此模式下[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)为 TRUE。  
  
##  <a name="ispointneardocksite"></a>  CDockingManager::IsPointNearDockSite  
 确定指定的点是否在停靠站点附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>参数  
 [in]*点*  
 指定的点。  
  
 [out]*dwBarAlignment*  
 指定的点是附近的边缘。 可能的值为 CBRS_ALIGN_LEFT、 CBRS_ALIGN_RIGHT、 CBRS_ALIGN_TOP 和 CBRS_ALIGN_BOTTOM。  
  
 [out]*bOuterEdge*  
 在点附近的外边框的停靠站点中; 如果为 TRUEFALSE 否则为。  
  
### <a name="return-value"></a>返回值  
 在点附近停靠站点中; 如果为 TRUE否则为 FALSE。  
  
##  <a name="isprintpreviewvalid"></a>  CDockingManager::IsPrintPreviewValid  
 确定是否设置打印预览模式。  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果打印预览模式设置; 则为 TRUEFALSE 否则为。  
  
##  <a name="loadstate"></a>  CDockingManager::LoadState  
 从注册表加载到停靠管理器的状态。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszProfileName*  
 配置文件名称。  
  
 [in]*uiID*  
 到停靠管理器的 id。  
  
### <a name="return-value"></a>返回值  
 如果停靠管理器状态加载成功，则为 TRUE否则为 FALSE。  
  
##  <a name="lockupdate"></a>  CDockingManager::LockUpdate  
 将锁定给定的窗口。  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>参数  
 [in]*块*  
 如果窗口被锁定，则为 TRUEFALSE 否则为。  
  
### <a name="remarks"></a>备注  
 当一个窗口处于锁定状态时，不能移动并不能重绘。  
  
##  <a name="m_bhidedockingbarsincontainermode"></a>  CDockingManager::m_bHideDockingBarsInContainerMode  
 指定是否停靠管理器将隐藏在 OLE 容器模式下的窗格。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>备注  
 如果你想要保留所有窗格停靠到主框架可见 OLE 容器模式应用程序时，请将此值设置为 FALSE。 默认情况下，此值为 TRUE。  
  
##  <a name="m_dockmodeglobal"></a>  CDockingManager::m_dockModeGlobal  
 指定的全局停靠模式。  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，每个停靠窗格使用此停靠模式。 此字段可以设置为值的详细信息，请参阅[cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode)。  
  
##  <a name="m_ndocksensitivity"></a>  CDockingManager::m_nDockSensitivity  
 指定停靠的敏感度。  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>备注  
 停靠敏感度定义如何关闭浮动窗格可在 framework 更改其状态以停靠之前接近停靠窗格、 停靠站点或另一个窗格。  
  
##  <a name="m_ntimeoutbeforedockingbardock"></a>  CDockingManager::m_nTimeOutBeforeDockingBarDock  
 指定以毫秒为单位之前停靠窗格停靠在立即停靠模式下, 的时间。  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>备注  
 停靠窗格之前，框架将等待指定的时间长度。 这可以防止在窗格时仍正在拖动意外停靠到的位置。  
  
##  <a name="m_ntimeoutbeforetoolbardock"></a>  CDockingManager::m_nTimeOutBeforeToolBarDock  
 指定以毫秒为单位之前工具栏停靠到主框架窗口, 的时间。  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>备注  
 工具栏停靠之前，框架将等待指定的时间长度。 这可以防止工具栏时仍正在拖动意外停靠到的位置。  
  
##  <a name="onactivateframe"></a>  CDockingManager::OnActivateFrame  
 框架窗口使处于活动状态或停用时由框架调用。  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in]*bActivate*  
 如果为 TRUE，框架窗口使处于活动状态;如果为 FALSE，将停用的框架窗口。  
  
##  <a name="onclosepopupmenu"></a>  CDockingManager::OnClosePopupMenu  
 当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>备注  
 它即将关闭当前的主窗口时，框架将发送 WM_DESTROY 消息。 重写此方法以处理来自通知`CMFCPopupMenu`属于框架窗口的对象时`CMFCPopupMenu`对象处理 WM_DESTROY 消息。  
  
##  <a name="onmoveminiframe"></a>  CDockingManager::OnMoveMiniFrame  
 由框架调用以移动微型框架窗口。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 [in]*pFrame*  
 指向微型框架窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 TRUE否则为 FALSE。  
  
##  <a name="onpanecontextmenu"></a>  CDockingManager::OnPaneContextMenu  
 生成具有一组窗格菜单时由框架调用。  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in]*点*  
 指定菜单的位置。  
  
##  <a name="panefrompoint"></a>  CDockingManager::PaneFromPoint  
 返回包含给定的点的窗格。  
  
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
 [in]*点*  
 指定以屏幕坐标，以检查点。  
  
 [in]*nSensitivity*  
 要放大量窗口矩形的每个选中的窗格中的值。 如果给定的点在此增加的区域，窗格满足搜索条件。  
  
 [in]*bExactBar*  
 为 true，则忽略*nSensitivity*参数; 否则为 FALSE。  
  
 [in]*pRTCBarType*  
 如果不为 NULL，则方法会搜索仅指定类型的窗格。  
  
 [in]*bCheckVisibility*  
 为 TRUE，则检查仅可见窗格;否则为 FALSE。  
  
 [out]*dwAlignment*  
 如果指定点处找到一个窗格，则此参数将包含已接近指定点在窗格一侧。 有关详细信息，请参阅“备注”部分。  
  
 [in]*pBarToIgnore*  
 如果不为 NULL，该方法将忽略此参数指定的窗格。  
  
### <a name="return-value"></a>返回值  
 [CBasePane](../../mfc/reference/cbasepane-class.md)-派生的对象，包含给定的时间，则为 NULL，如果不找到任何窗格。  
  
### <a name="remarks"></a>备注  
 该函数将返回并找到一个窗格时, *dwAlignment*包含指定点的对齐方式。 例如，如果点为最接近的窗格中，顶部*dwAlignment*设置为 CBRS_ALIGN_TOP。  
  
##  <a name="processpanecontextmenucommand"></a>  CDockingManager::ProcessPaneContextMenuCommand  
 由框架调用以选择或以清除复选框为指定的命令并重新计算显示窗格的布局。  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 [in]*nID*  
 在菜单中的控件条的 id。  
  
 [in]*nCode*  
 命令通知代码。  
  
 [in]*pExtra*  
 指向 void 的指针是强制转换为一个指向`CCmdUI`如果*nCode*是 CN_UPDATE_COMMAND_UI。  
  
 [in]*pHandlerInfo*  
 指向信息结构的指针。 未使用此参数。  
  
### <a name="return-value"></a>返回值  
 则为 TRUE *pEXtra*不为 NULL 并*nCode*等于 CN_UPDATE_COMMAND_UI，或如果没有具有指定的控件条*nID*。  
  
##  <a name="recalclayout"></a>  CDockingManager::RecalcLayout  
 重新计算的控件列表中存在的控件的内部布局。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bNotify*  
 未使用此参数。  
  
##  <a name="releaseemptypanecontainers"></a>  CDockingManager::ReleaseEmptyPaneContainers  
 释放空窗格容器。  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="removehiddenmditabbedbar"></a>  CDockingManager::RemoveHiddenMDITabbedBar  
 移除指定的隐藏栏窗格。  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBar*  
 指向一个栏的窗格中删除。  
  
##  <a name="removeminiframe"></a>  CDockingManager::RemoveMiniFrame  
 从微型框架的列表中删除指定的范围。  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in]*pWnd*  
 指向要删除的帧的指针。  
  
### <a name="return-value"></a>返回值  
 如果指定的范围被删除; 则为 TRUEFALSE 否则为。  
  
##  <a name="removepanefromdockmanager"></a>  CDockingManager::RemovePaneFromDockManager  
 注销一个窗格，并将其从列表中到停靠管理器删除。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pWnd,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*pWnd*  
 指向要删除一个窗格的指针。  
  
 [in]*bDestroy*  
 如果为 TRUE，将销毁已删除的窗格。  
  
 [in]*bAdjustLayout*  
 如果为 TRUE，则立即调整停靠布局。  
  
 [in]*bAutoHide*  
 如果为 TRUE，在窗格是从自动隐藏栏列表中删除。 如果为 FALSE，窗格中已从的正则窗格的列表。  
  
 [in]*pBarReplacement*  
 指向一个窗格，它将替换已删除的窗格的指针。  
  
##  <a name="replacepane"></a>  CDockingManager::ReplacePane  
 用一个窗格替换另一个窗格。  
  
```  
BOOL ReplacePane(
    CDockablePane* pOriginalBar,  
    CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pOriginalBar*  
 指向原始的窗格的指针。  
  
 [in]*pNewBar*  
 指向将替换原始窗格的窗格的指针。  
  
### <a name="return-value"></a>返回值  
 如果已成功替换窗格; 则为 TRUEFALSE 否则为。  
  
##  <a name="resortminiframesforzorder"></a>  CDockingManager::ResortMiniFramesForZOrder  
 较微型框架的列表中的框架。  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="savestate"></a>  CDockingManager::SaveState  
 将停靠管理器的状态保存到注册表。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszProfileName*  
 对一个注册表项路径。  
  
 [in]*uiID*  
 停靠管理器 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则保存状态，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 保存到注册表到停靠管理器的状态涉及到将保存的状态的控件条、 自动隐藏栏的状态和最小的帧到停靠管理器中存在的状态。  
  
##  <a name="sendmessagetominiframes"></a>  CDockingManager::SendMessageToMiniFrames  
 将指定的消息发送到所有微型框架。  
  
```  
BOOL SendMessageToMiniFrames(
    UINT uMessage,  
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>参数  
 [in]*uMessage*  
 要发送的消息。  
  
 [in]*wParam*  
 更多的消息的相关信息。  
  
 [in]*lParam*  
 更多的消息的相关信息。  
  
### <a name="return-value"></a>返回值  
 始终为 TRUE。  
  
##  <a name="serialize"></a>  CDockingManager::Serialize  
 写入存档到停靠管理器。  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in]*ar*  
 对存档对象的引用。  
  
### <a name="remarks"></a>备注  
 到停靠管理器写入存档涉及到决定的停靠控件条和滑块，并编写到存档的控件条、 迷你帧、 自动隐藏栏和 MDI 选项卡式条数。  
  
##  <a name="setautohidezorder"></a>  CDockingManager::SetAutohideZOrder  
 设置大小、 宽度和高度的控件条和指定的窗格。  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>参数  
 [in]*pAHDockingBar*  
 指向可停靠窗格的指针。  
  
##  <a name="setdockingmode"></a>  CDockingManager::SetDockingMode  
 设置停靠模式。  
  
```  
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,  
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```  
  
### <a name="parameters"></a>参数  
 *dockMode*  
 指定新的停靠模式。 有关详细信息，请参阅“备注”部分。  
  
 *主题*  
 指定要用于智能停靠标记的主题。 它可以是下列枚举值之一： AFX_SDT_DEFAULT，AFX_SDT_VS2005，AFX_SDT_VS2008。  
  
### <a name="remarks"></a>备注  
 调用此静态方法以设置停靠模式。  
  
 *dockMode*可以是下列值之一：  
  
- DT_STANDARD-作为 Visual Studio.NET 2003年中实现的标准停靠模式。 窗格拖动而无需拖放的上下文中。  
  
- DT_IMMEDIATE-为 Microsoft Visio 中实现的即时停靠模式。 窗格拖动拖动上下文，但没有标记的显示。  
  
- DT_SMART-在 Visual Studio 2005 中实现智能停靠模式。 窗格拖动具有拖动上下文，并显示智能标记的显示窗格可以停靠位置。  
  
##  <a name="setdockstate"></a>  CDockingManager::SetDockState  
 设置停靠控件条、 最小的帧中，和自动隐藏栏的状态。  
  
```  
virtual void SetDockState();
```  
  
##  <a name="setprintpreviewmode"></a>  CDockingManager::SetPrintPreviewMode  
 设置的条形图的打印预览中显示打印预览模式。  
  
```  
void SetPrintPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>参数  
 [in]*bPreview*  
 如果打印预览模式设置; 则为 TRUEFALSE 否则为。  
  
 [in]*pState*  
 一个指向预览状态。 未使用此参数。  
  
##  <a name="setsmartdockingparams"></a>  CDockingManager::SetSmartDockingParams  
 设置用于定义智能停靠的行为的参数。  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>参数  
 [in、 out]*params*  
 定义智能停靠的参数。  
  
### <a name="remarks"></a>备注  
 如果你想要自定义外观、 颜色或智能停靠标记的形状，请调用此方法。  
  
 若要使用智能停靠标记的默认外观，未初始化的实例传递[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)到*params*。  
  
##  <a name="showdelayshowminiframes"></a>  CDockingManager::ShowDelayShowMiniFrames  
 显示或隐藏的微型框架窗口。  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>参数  
 [in]*bShow*  
 若要使所示的框架的窗口处于活动状态;为 FALSE，则隐藏为框架的窗口。  
  
##  <a name="showpanes"></a>  CDockingManager::ShowPanes  
 显示或隐藏的控件和自动隐藏栏的窗格。  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in]*bShow*  
 为 TRUE，则显示窗格;如果为 FALSE，则若要隐藏窗格。  
  
### <a name="return-value"></a>返回值  
 始终为 FALSE。  
  
##  <a name="startsdocking"></a>  CDockingManager::StartSDocking  
 启动智能停靠的智能停靠管理器的对齐方式根据指定的窗口。  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDockingWnd*  
 指向要停靠的窗口的指针。  
  
##  <a name="stopsdocking"></a>  CDockingManager::StopSDocking  
 停止智能停靠。  
  
```  
void StopSDocking();
```  
  
##  <a name="getsmartdockingtheme"></a>  CDockingManager::GetSmartDockingTheme  
 返回一个用来显示智能停靠标记的主题的静态方法。  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>返回值  
 返回下列枚举值之一： AFX_SDT_DEFAULT，AFX_SDT_VS2005，AFX_SDT_VS2008。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)
