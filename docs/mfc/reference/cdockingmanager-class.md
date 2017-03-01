---
title: "CDockingManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockingManager
dev_langs:
- C++
helpviewer_keywords:
- CDockingManager class
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 106046dc9dc671b5baea7c6df78b91ba37098978
ms.lasthandoff: 02/24/2017

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
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|向栏中添加一个句柄到隐藏的 MDI 选项卡式工具栏窗格的列表窗格。|  
|[CDockingManager::AddMiniFrame](#addminiframe)|最小的框架的列表中添加一个框架。|  
|[CDockingManager::AddPane](#addpane)|注册的扩展管理器窗格。|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|重新计算和调整的布局框架窗口中的所有窗格。|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|导致`WM_NCCALCSIZE`消息发送到所有窗格和`CPaneFrameWnd`windows。|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|调整的矩形的对齐方式。|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|调整在自动隐藏模式下的停靠窗格大小，以便它采用全角或括在框架的工作区的高度停靠站点。|  
|[CDockingManager::AutoHidePane](#autohidepane)|创建的自动隐藏工具栏。|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|将具有到文件的顶部指定的对齐方式的停靠的栏。|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|向菜单添加的停靠窗格和工具栏的名称。|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|计算停靠窗口的预期的矩形。|  
|[CDockingManager::Create](#create)|创建一个扩展管理器。|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|确定，其中包含给定的点和其停靠状态窗格。|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|启用或禁用加载注册表中的停靠布局。|  
|[CDockingManager::DockPane](#dockpane)|窗格停靠到另一个窗格或框架窗口。|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|将窗格停靠到另一个窗格的左侧。|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|使窗格的停靠到主框架，创建一个停靠窗格中，并将其添加到控件条的列表。|  
|[CDockingManager::EnableDocking](#enabledocking)|创建一个停靠窗格，并启用窗格中的停靠到主框架。|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|显示一个额外的按钮打开所有的停靠窗格的标题上的弹出菜单。|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|通知库以显示有一个应用程序工具栏和停靠窗格的列表，当用户单击鼠标右键，库正在处理 WM_CONTEXTMENU 消息的特殊的上下文菜单。|  
|[CDockingManager::FindDockSite](#finddocksite)|检索栏窗格中位于指定位置且具有指定的对齐方式。|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|返回的条 id 为目标栏窗格中的窗格。|  
|[CDockingManager::FindPaneByID](#findpanebyid)|查找一个窗格，通过指定的控件 id。|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|提交到虚拟矩形的所有当前工具栏位置。|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|返回包含给定的点的帧。|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|获取包含的客户端区域的边界的矩形。|  
|[CDockingManager::GetDockingMode](#getdockingmode)|返回当前扩展模式。|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|获取一个指针指向父窗口框架。|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|返回窗格的启用对齐方式。|  
|[CDockingManager::GetMiniFrames](#getminiframes)|获取小型机的列表。|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|获取包含框架的外边缘的矩形。|  
|[CDockingManager::GetPaneList](#getpanelist)|返回属于扩展管理器窗格的列表。 这包括所有浮动窗格。|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|检索指向智能停靠管理器的指针。|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|检索指向智能停靠管理器的指针。|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|返回停靠 manager 智能停靠参数。|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|返回一个用来显示智能停靠标记的主题的静态方法。|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|隐藏在自动隐藏模式下的窗格。|  
|[CDockingManager::InsertDockSite](#insertdocksite)|创建停靠窗格中，并将其插入到控件条的列表。|  
|[CDockingManager::InsertPane](#insertpane)|控件条的列表中插入控件窗格。|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|指定是否在所有窗格的标题上显示一个弹出菜单。|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|确定是否调整所有窗格的布局。|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|指定的扩展管理器是否在 OLE 容器模式下。|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|确定指定的点是否在停靠站点附近。|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|确定是否设置了打印预览模式。|  
|[CDockingManager::LoadState](#loadstate)|从注册表加载的扩展管理器的状态。|  
|[CDockingManager::LockUpdate](#lockupdate)|将锁定给定的窗口。|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|框架窗口设为活动或停用时由框架调用。|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|由框架要移动的微型框架窗口调用。|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|在构建一个菜单，有一个窗格的列表时，由框架调用。|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|返回包含给定的点的窗格。|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|由框架来选择或清除复选框为指定的命令，并重新计算布局的显示窗格中调用。|  
|[CDockingManager::RecalcLayout](#recalclayout)|重新计算存在于列表中的控件的控件的内部布局。|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|释放空的窗格中的容器。|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|移除指定的栏窗格中隐藏。|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|从最小的框架的列表中移除指定的范围。|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|注销一个窗格，并将其从列表中的扩展管理器中删除。|  
|[CDockingManager::ReplacePane](#replacepane)|用一个窗格替换另一个窗格。|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|将微型框架的列表中的帧重新排序。|  
|[CDockingManager::SaveState](#savestate)|将扩展管理器的状态保存到注册表。|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|将指定的消息发送到所有的微型框架。|  
|[CDockingManager::Serialize](#serialize)|扩展管理器写入存档。 (重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|设置大小、 宽度和高度的控制条和指定窗格。|  
|[CDockingManager::SetDockingMode](#setdockingmode)|设置停靠的模式。|  
|[CDockingManager::SetDockState](#setdockstate)|设置停靠控件条、 最小的帧中，和自动隐藏条形图的状态。|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|设置的条形图的打印预览中显示打印预览模式。|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|设置定义智能停靠的行为的参数。|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|显示或隐藏的微型框架窗口。|  
|[CDockingManager::ShowPanes](#showpanes)|显示或隐藏控制和自动隐藏条形图的窗格。|  
|[CDockingManager::StartSDocking](#startsdocking)|启动智能停靠所指定的窗口根据智能停靠管理器的对齐方式。|  
|[CDockingManager::StopSDocking](#stopsdocking)|停止智能停靠。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|指定是否停靠 manager 隐藏在 OLE 容器模式中的窗格。|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|指定的全局停靠模式。|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|指定停靠区分大小写。|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|停靠窗格即停靠在停靠即时模式之前，请指定的时间，以毫秒为单位。|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|指定的时间，以毫秒为单位，前一个工具栏停靠到主框架窗口。|  
  
## <a name="remarks"></a>备注  
 主框架窗口创建并自动初始化此类。  
  
 停靠的管理器对象保留在停靠布局中的所有窗格的列表以及所有的列表[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)属于主框架窗口的窗口。  
  
 `CDockingManager`类实现可用于查找窗格某些服务或`CPaneFrameWnd`窗口。 您通常不这些服务直接调用因为包装在主框架窗口对象。 有关详细信息，请参阅[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)。  
  
## <a name="customization-tips"></a>自定义提示  
 以下提示适用于`CDockingManager`对象︰  
  
- [CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)支持这些停靠模式︰  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     这些停靠模式由[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)并通过调用设置[CDockingManager::SetDockingMode](#setdockingmode)。  
  
-   如果您想要创建非浮点的、 非大小可调的窗格中，调用[CDockingManager::AddPane](#addpane)方法。 此方法负责窗格中的布局在扩展管理器注册窗格。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CDockingManager`用于配置类`CDockingManager`对象。 该示例演示如何显示一个额外的按钮将打开一个弹出菜单上的所有停靠窗格的标题，以及如何设置该对象的停靠模式。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&24;](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxDockingManager.h  
  
##  <a name="a-nameadddocksitea--cdockingmanageradddocksite"></a><a name="adddocksite"></a>CDockingManager::AddDockSite  
 创建一个停靠窗格并将其添加到控件条的列表。  
  
```  
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `info`  
 对包含信息结构的引用将停靠窗格中的对齐方式。  
  
 [out] `ppDockBar`  
 指向新的停靠窗格的指针指向的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建的停靠窗格`FALSE`否则为。  
  
##  <a name="a-nameaddhiddenmditabbedbara--cdockingmanageraddhiddenmditabbedbar"></a><a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar  
 向栏中添加一个句柄到隐藏的 MDI 选项卡式工具栏窗格的列表窗格。  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向一个栏窗格  
  
##  <a name="a-nameaddpanea--cdockingmanageraddpane"></a><a name="addpane"></a>CDockingManager::AddPane  
 注册的扩展管理器窗格。  
  
```  
BOOL AddPane(
    CBasePane* pWnd,  
    BOOL bTail = TRUE,  
    BOOL bAutoHide = FALSE,  
    BOOL bInsertForOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pWnd`  
 指定将添加到停靠管理器窗格。  
  
 [in] `bTail`  
 `TRUE`可以为扩展管理器; 窗格的列表的末尾添加窗格中否则为`FALSE`。  
  
 [in] `bAutoHide`  
 仅限内部使用。 始终使用默认值`FALSE`。  
  
 [in] `bInsertForOuterEdge`  
 仅限内部使用。 始终使用默认值`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中已成功注册到停靠的管理器;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以扩展管理器中注册非浮点的、 非大小可调的窗格。 如果您没有注册窗格中，它们将无法正确显示时的扩展管理器的布局方式。  
  
##  <a name="a-nameadjustdockinglayouta--cdockingmanageradjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout  
 重新计算和调整的布局框架窗口中的所有窗格。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `hdwp`  
 指定延迟的窗口位置结构。 有关详细信息，请参阅[Windows 数据类型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddminiframea--cdockingmanageraddminiframe"></a><a name="addminiframe"></a>CDockingManager::AddMiniFrame  
 最小的框架的列表中添加一个框架。  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指向一个帧的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果帧未处于微型框架的列表，并且已成功，则添加`FALSE`否则为。  
  
##  <a name="a-nameadjustpaneframesa--cdockingmanageradjustpaneframes"></a><a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames  
 导致`WM_NCCALCSIZE`消息发送到所有窗格和`CPaneFrameWnd`windows。  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameadjustrecttoclientareaa--cdockingmanageradjustrecttoclientarea"></a><a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea  
 调整的矩形的对齐方式。  
  
```  
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectResult`  
 对引用`CRect`对象  
  
 [in] `dwAlignment`  
 对齐方式`CRect`对象  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果的对齐方式`CRect`对象进行调整。`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 `dwAlignment`参数可以具有下列值之一︰  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="a-namealignautohidepanea--cdockingmanageralignautohidepane"></a><a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane  
 调整在自动隐藏模式下的停靠窗格大小，以便它采用全角或括在框架的工作区的高度停靠站点。  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDefaultSlider`  
 滑块的停靠窗格。  
  
 [in] `bIsVisible`  
 `TRUE`如果停靠窗格中可见;`FALSE`否则为。  
  
##  <a name="a-nameautohidepanea--cdockingmanagerautohidepane"></a><a name="autohidepane"></a>CDockingManager::AutoHidePane  
 创建的自动隐藏工具栏。  
  
```  
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,  
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指针到栏窗格。  
  
 [in] `pCurrAutoHideToolBar`  
 指向自动隐藏工具栏的指针。  
  
### <a name="return-value"></a>返回值  
 `NULL`如果自动隐藏工具栏不被创建;否则为指向新的工具栏。  
  
##  <a name="a-namebringbarstotopa--cdockingmanagerbringbarstotop"></a><a name="bringbarstotop"></a>CDockingManager::BringBarsToTop  
 将具有到文件的顶部指定的对齐方式的停靠的栏。  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 停靠条形图的将转到其他窗口的顶部对齐方式。  
  
 [in] `bExcludeDockedBars`  
 `TRUE`要从在最前面; 已排除停靠的栏否则为`FALSE`。  
  
##  <a name="a-namebuildpanesmenua--cdockingmanagerbuildpanesmenu"></a><a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu  
 向菜单添加的停靠窗格和工具栏的名称。  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>参数  
 [in] `menu`  
 要添加的停靠窗格和工具栏停靠在名称中的菜单。  
  
 [in] `bToolbarsOnly`  
 `TRUE`若要将仅工具栏名称添加到菜单;`FALSE`否则为。  
  
##  <a name="a-namecalcexpecteddockedrecta--cdockingmanagercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect  
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
 [in] `pWnd`  
 指向窗口停靠的指针。  
  
 [in] `ptMouse`  
 鼠标的位置。  
  
 [out] `rectResult`  
 计算的矩形。  
  
 [in] `bDrawTab`  
 `TRUE`若要绘制一个选项卡;否则为`FALSE`。  
  
 [out] `ppTargetBar`  
 指向目标窗格中的指针指向的指针。  
  
### <a name="remarks"></a>备注  
 此方法计算一个窗口，如果用户拖动到所指定的点窗口中所占用的矩形`ptMouse`而存在停靠。  
  
##  <a name="a-namecreatea--cdockingmanagercreate"></a><a name="create"></a>CDockingManager::Create  
 创建一个扩展管理器。  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 指向扩展管理器的父框架的指针。 此值不能`NULL`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`始终。  
  
##  <a name="a-namedeterminepaneandstatusa--cdockingmanagerdeterminepaneandstatus"></a><a name="determinepaneandstatus"></a>CDockingManager::DeterminePaneAndStatus  
 确定，其中包含给定的点和其停靠状态窗格。  
  
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
 [in] `pt`  
 要检查的窗格的位置。  
  
 [in] `nSensitivity`  
 要增加每个选中的窗格中的窗口矩形的值。 如果给定的点在此增加的区域中，一个窗格满足搜索条件。  
  
 [in] `dwEnabledAlignment`  
 停靠窗格中的对齐方式。  
  
 [out] `ppTargetBar`  
 指向目标窗格中的指针指向的指针。  
  
 [in] `pBarToIgnore`  
 窗格中，该方法将忽略。  
  
 [in] `pBarToDock`  
 停靠窗格。  
  
### <a name="return-value"></a>返回值  
 停靠状态。  
  
### <a name="remarks"></a>备注  
 停靠状态可以是下列值之一︰  
  
|AFX_CS_STATUS 值|含义|  
|---------------------------|-------------|  
|CS_NOTHING|指针不在停靠站点中。 因此，应保持窗格中浮动。|  
|CS_DOCK_IMMEDIATELY|在即时模式中的停靠站点上 （启用 DT_IMMEDIATE 样式），因此必须立即停靠窗格。|  
|CS_DELAY_DOCK|指针位于停靠站点是另一个的停靠窗格或边缘的主框架。|  
|CS_DELAY_DOCK_TO_TAB|指针位于上导致窗格停靠在选项卡式窗口停靠站点。 鼠标位于通过另一个的停靠窗格的标题或选项卡式窗格中的选项卡区域时，将发生这种情况。|  
  
##  <a name="a-namedisablerestoredockstatea--cdockingmanagerdisablerestoredockstate"></a><a name="disablerestoredockstate"></a>CDockingManager::DisableRestoreDockState  
 启用或禁用加载注册表中的停靠布局。  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDisable`  
 `TRUE`禁用从注册表中; 停靠布局的加载否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当加载应用程序状态时，必须保留当前布局的停靠窗格和工具栏，请调用此方法。  
  
##  <a name="a-namedockpanea--cdockingmanagerdockpane"></a><a name="dockpane"></a>CDockingManager::DockPane  
 窗格停靠到另一个窗格或框架窗口。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向一个栏的停靠窗格。  
  
 [in] `nDockBarID`  
 栏，停靠的 id。  
  
 [in] `lpRect`  
 目标矩形中。  
  
##  <a name="a-namedockpaneleftofa--cdockingmanagerdockpaneleftof"></a><a name="dockpaneleftof"></a>CDockingManager::DockPaneLeftOf  
 将窗格停靠到另一个窗格的左侧。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBarToDock`  
 为停靠在左侧窗格中的指针`pTargetBar`。  
  
 [in] `pTargetBar`  
 指向目标窗格中的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠窗格，否则为`FALSE`。  
  
##  <a name="a-nameenableautohidepanesa--cdockingmanagerenableautohidepanes"></a><a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes  
 使窗格的停靠到主框架，创建一个停靠窗格中，并将其添加到控件条的列表。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwStyle`  
 停靠的对齐方式。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建的停靠窗格`FALSE`否则为。  
  
##  <a name="a-nameenabledockinga--cdockingmanagerenabledocking"></a><a name="enabledocking"></a>CDockingManager::EnableDocking  
 创建一个停靠窗格，并启用窗格中的停靠到主框架。  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwStyle`  
 停靠的对齐方式。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建的停靠窗格`FALSE`否则为。  
  
##  <a name="a-nameenabledocksitemenua--cdockingmanagerenabledocksitemenu"></a><a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu  
 显示一个额外的按钮打开所有的停靠窗格的标题上的弹出菜单。  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用停靠站点菜单;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 停靠站点菜单会显示用于更改窗格中的插接状态的以下选项︰  
  
- `Floating`-浮动窗格  
  
- `Docking`-在主框架中一次停靠窗格中的位置窗格的停靠  
  
- `AutoHide`-窗格中切换到自动隐藏模式  
  
- `Hide`-隐藏窗格  
  
 默认情况下，不显示此菜单。  
  
##  <a name="a-nameenablepanecontextmenua--cdockingmanagerenablepanecontextmenu"></a><a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu  
 通知库以显示有一个应用程序工具栏和停靠窗格的列表，当用户单击鼠标右键，库正在处理 WM_CONTEXTMENU 消息的特殊的上下文菜单。  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 如果`TRUE`，库打开的支持自动的上下文菜单; 如果`FALSE`库关闭自动上下文菜单的支持。  
  
 [in] `uiCustomizeCmd`  
 命令 id**自定义**菜单中的项。  
  
 [in] `strCustomizeText`  
 文本**自定义**项。  
  
 [in] `bToolbarsOnly`  
 如果`TRUE`，菜单中只显示列表的应用程序工具栏; 如果`FALSE`，库将应用程序的停靠窗格添加到此列表。  
  
##  <a name="a-namefinddocksitea--cdockingmanagerfinddocksite"></a><a name="finddocksite"></a>CDockingManager::FindDockSite  
 检索栏窗格中位于指定位置且具有指定的对齐方式。  
  
```  
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,  
    BOOL bOuter);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 条的对齐方式窗格。  
  
 [in] `bOuter`  
 如果`TRUE`，检索列表中的控件条的头位置中的栏。 否则，检索在列表中的控件条的结尾位置栏。  
  
### <a name="return-value"></a>返回值  
 具有指定的对齐方式; 停靠窗格`NULL`否则为。  
  
##  <a name="a-namefindpanebyida--cdockingmanagerfindpanebyid"></a><a name="findpanebyid"></a>CDockingManager::FindPaneByID  
 查找一个窗格，通过指定的控件 id。  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uBarID`  
 指定要查找窗格中的控件 ID。  
  
 [in] `bSearchMiniFrames`  
 `TRUE`若要在搜索中包括所有浮动窗格。 `FALSE`若要包括仅停靠的窗格。  
  
### <a name="return-value"></a>返回值  
 [CBasePane](../../mfc/reference/cbasepane-class.md)具有指定的控件 ID 的对象或`NULL`如果找不到指定的窗格。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namefinddocksitebypanea--cdockingmanagerfinddocksitebypane"></a><a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane  
 返回的条 id 为目标栏窗格中的窗格。  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTargetBar`  
 指向目标状态栏窗格中的指针。  
  
### <a name="return-value"></a>返回值  
 栏窗格，它具有的 id 的目标栏窗格中;`NULL`如果没有此类栏窗格中存在。  
  
##  <a name="a-namefixupvirtualrectsa--cdockingmanagerfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects  
 提交到虚拟矩形的所有当前工具栏位置。  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>备注  
 当用户开始拖动一个工具栏时，该应用程序会记住中的其原始位置*虚拟矩形*。 当用户在其停靠站点之间移动一个工具栏时，工具栏可能会发生移动其他工具栏。 其他工具栏的原始位置存储在相应的虚拟矩形中。  
  
##  <a name="a-nameframefrompointa--cdockingmanagerframefrompoint"></a><a name="framefrompoint"></a>CDockingManager::FrameFromPoint  
 返回包含给定的点的帧。  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pt`  
 指定在屏幕坐标中，若要检查该点。  
  
 [in] `pFrameToExclude`  
 指向要排除的帧的指针。  
  
 [in] `bFloatMultiOnly`  
 `TRUE`要排除不是的实例的帧`CMultiPaneFrameWnd`;`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 包含给定的点; 的框架。`NULL`否则为。  
  
##  <a name="a-namegetclientareaboundsa--cdockingmanagergetclientareabounds"></a><a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds  
 获取包含的客户端区域的边界的矩形。  
  
```  
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```  
  
### <a name="parameters"></a>参数  
 [out] `rcClient`  
 对包含的客户端区域的边界的矩形的引用。  
  
### <a name="return-value"></a>返回值  
 包含客户端区域的边界的矩形。  
  
##  <a name="a-namegetdockingmodea--cdockingmanagergetdockingmode"></a><a name="getdockingmode"></a>CDockingManager::GetDockingMode  
 返回当前扩展模式。  
  
```  
static AFX_DOCK_TYPE GetDockingMode();
```  
  
### <a name="return-value"></a>返回值  
 一个表示当前停靠模式的枚举器值。 它可以是下列值之一︰  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
### <a name="remarks"></a>备注  
 若要设置停靠模式，请调用[CDockingManager::SetDockingMode](#setdockingmode)。  
  
##  <a name="a-namegetdocksiteframewnda--cdockingmanagergetdocksiteframewnd"></a><a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd  
 获取一个指针指向父窗口框架。  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向父窗口框架的指针。  
  
##  <a name="a-namegetenabledautohidealignmenta--cdockingmanagergetenabledautohidealignment"></a><a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment  
 返回窗格的启用对齐方式。  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>返回值  
 按位组合`CBRS_ALIGN_`标志，则为 0，如果未启用自动隐藏窗格。 有关详细信息，请参阅[CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking)。  
  
### <a name="remarks"></a>备注  
 该方法返回的已启用自动隐藏控件条对齐方式。 若要启用自动隐藏条形图，请调用[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)。  
  
##  <a name="a-namegetminiframesa--cdockingmanagergetminiframes"></a><a name="getminiframes"></a>CDockingManager::GetMiniFrames  
 获取小型机的列表。  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含属于扩展管理器的控制条小型机的列表。  
  
##  <a name="a-namegetouteredgeboundsa--cdockingmanagergetouteredgebounds"></a><a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds  
 获取包含框架的外边缘的矩形。  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含框架的外边缘的矩形。  
  
##  <a name="a-namegetpanelista--cdockingmanagergetpanelist"></a><a name="getpanelist"></a>CDockingManager::GetPaneList  
 返回属于扩展管理器窗格的列表。 这包括所有浮动窗格。  
  
```  
void GetPaneList(
    CObList& lstBars,  
    BOOL bIncludeAutohide = FALSE,  
    CRuntimeClass* pRTCFilter = NULL,  
    BOOL bIncludeTabs = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `lstBars`  
 包含当前扩展管理器的所有窗格。  
  
 [in] `bIncludeAutohide`  
 `TRUE`若要包括在自动隐藏模式; 显示窗格否则为`FALSE`。  
  
 [in] `pRTCFilter`  
 如果不是`NULL`，返回的列表包含仅指定的运行时类的窗格。  
  
 [in] `bIncludeTabs`  
 `TRUE`若要包括选项卡。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果在扩展管理器中有任何选项卡式的窗格，该方法返回指向[CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)对象，并且您必须显式枚举选项卡。  
  
 使用`pRTCFilter`若要获取的特定类的窗格。 例如，通过适当地设置此值可以获得仅工具栏。  
  
##  <a name="a-namegetsmartdockingmanagera--cdockingmanagergetsmartdockingmanager"></a><a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager  
 检索指向智能停靠管理器的指针。  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>返回值  
 一个指向[智能停靠 manager](http://msdn.microsoft.com/en-us/f537a1a6-fb9e-41d7-952f-0f25d5ee7534)。  
  
##  <a name="a-namegetsmartdockingmanagerpermanenta--cdockingmanagergetsmartdockingmanagerpermanent"></a><a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent  
 检索指向智能停靠管理器的指针。  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>返回值  
 智能停靠管理器指向的指针。  
  
##  <a name="a-namegetsmartdockingparamsa--cdockingmanagergetsmartdockingparams"></a><a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams  
 返回停靠 manager 智能停靠参数。  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>返回值  
 当前的扩展管理器包含智能停靠参数的类。 有关详细信息，请参阅[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehideautohidepanesa--cdockingmanagerhideautohidepanes"></a><a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes  
 隐藏在自动隐藏模式下的窗格。  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBarToExclude`  
 指向一个条，以便排除隐藏的指针。  
  
 [in] `bImmediately`  
 `TRUE`若要立即; 隐藏窗格`FALSE`隐藏的自动隐藏效果窗格。  
  
##  <a name="a-nameinsertdocksitea--cdockingmanagerinsertdocksite"></a><a name="insertdocksite"></a>CDockingManager::InsertDockSite  
 创建停靠窗格中，并将其插入到控件条的列表。  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `info`  
 包含有关停靠窗格中的对齐信息的结构。  
  
 [in] `dwAlignToInsertAfter`  
 停靠窗格中的对齐方式。  
  
 [out] `ppDockBar`  
 指向到停靠窗格中的指针的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建的停靠窗格`FALSE`否则为。  
  
##  <a name="a-nameinsertpanea--cdockingmanagerinsertpane"></a><a name="insertpane"></a>CDockingManager::InsertPane  
 控件条的列表中插入控件窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pControlBar`  
 指向控件窗格中的指针。  
  
 [in] `pTarget`  
 指向目标窗格中的指针。  
  
 [in] `bAfter`  
 `TRUE`要在目标窗格中; 的位置后插入窗格中`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果控件窗格中已成功添加到列表中的控件条;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 如果控件窗格中已在列表中的控件条或控件条的列表中不存在目标窗格中，此方法返回 false。  
  
##  <a name="a-nameisdocksitemenua--cdockingmanagerisdocksitemenu"></a><a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu  
 指定是否在所有窗格的标题上显示一个弹出菜单。  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果停靠站点菜单显示在标题的所有停靠窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 您可以通过调用启用停靠站点菜单[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)。  
  
##  <a name="a-nameisinadjustlayouta--cdockingmanagerisinadjustlayout"></a><a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout  
 确定是否调整所有窗格的布局。  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果调整所有窗格的布局，则;`FALSE`否则为。  
  
##  <a name="a-nameisolecontainermodea--cdockingmanagerisolecontainermode"></a><a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode  
 指定的扩展管理器是否在 OLE 容器模式下。  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果停靠管理器处于 OLE 容器模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在 OLE 容器模式下，隐藏所有停靠窗格和应用程序工具栏。 如果您已设置窗格窗格也会隐藏在此模式下[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)到`TRUE`。  
  
##  <a name="a-nameispointneardocksitea--cdockingmanagerispointneardocksite"></a><a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite  
 确定指定的点是否在停靠站点附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定的点。  
  
 [out] `dwBarAlignment`  
 指定的点是附近的边缘。 可能值为 `CBRS_ALIGN_LEFT`、`CBRS_ALIGN_RIGHT`、`CBRS_ALIGN_TOP` 和 `CBRS_ALIGN_BOTTOM`。  
  
 [out] `bOuterEdge`  
 `TRUE`如果该点附近的外边框的停靠站点中;`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该点附近停靠站点中;否则为`FALSE`。  
  
##  <a name="a-nameisprintpreviewvalida--cdockingmanagerisprintpreviewvalid"></a><a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid  
 确定是否设置了打印预览模式。  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果打印预览模式设置;`FALSE`否则为。  
  
##  <a name="a-nameloadstatea--cdockingmanagerloadstate"></a><a name="loadstate"></a>CDockingManager::LoadState  
 从注册表加载的扩展管理器的状态。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 配置文件名称。  
  
 [in] `uiID`  
 扩展管理器的 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则加载插接管理器状态否则为`FALSE`。  
  
##  <a name="a-namelockupdatea--cdockingmanagerlockupdate"></a><a name="lockupdate"></a>CDockingManager::LockUpdate  
 将锁定给定的窗口。  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>参数  
 [in] `bLock`  
 `TRUE`如果该窗口处于锁定状态;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 当窗口处于锁定状态时，就不会移动并不能重绘。  
  
##  <a name="a-namembhidedockingbarsincontainermodea--cdockingmanagermbhidedockingbarsincontainermode"></a><a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode  
 指定是否停靠 manager 隐藏在 OLE 容器模式中的窗格。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>备注  
 将此值设置为`FALSE`如果想要保留所有窗格停靠在主框架可见应用程序时在 OLE 容器模式下。 默认情况下，此值是`TRUE`。  
  
##  <a name="a-namemdockmodeglobala--cdockingmanagermdockmodeglobal"></a><a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal  
 指定的全局停靠模式。  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，每个停靠窗格中使用此停靠模式。 有关此字段可以设置为的值的详细信息，请参阅[CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)。  
  
##  <a name="a-namemndocksensitivitya--cdockingmanagermndocksensitivity"></a><a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity  
 指定停靠区分大小写。  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>备注  
 停靠的区分大小写定义如何关闭浮动窗格可以接触停靠窗格、 停靠站点或另一个窗格框架更改其状态，以停靠之前。  
  
##  <a name="a-namemntimeoutbeforedockingbardocka--cdockingmanagermntimeoutbeforedockingbardock"></a><a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock  
 停靠窗格即停靠在停靠即时模式之前，请指定的时间，以毫秒为单位。  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>备注  
 停靠窗格之前，框架将等待指定的时间长度。 这样可以防止窗格中时仍拖动意外停靠到的位置。  
  
##  <a name="a-namemntimeoutbeforetoolbardocka--cdockingmanagermntimeoutbeforetoolbardock"></a><a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock  
 指定的时间，以毫秒为单位，前一个工具栏停靠到主框架窗口。  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>备注  
 停靠工具栏之前，框架将等待指定的时间长度。 这样可以防止工具栏时仍拖动意外停靠到的位置。  
  
##  <a name="a-nameonactivateframea--cdockingmanageronactivateframe"></a><a name="onactivateframe"></a>CDockingManager::OnActivateFrame  
 框架窗口设为活动或停用时由框架调用。  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActivate`  
 如果`TRUE`，框架窗口设为活动; 如果`FALSE`，框架窗口停用。  
  
##  <a name="a-nameonclosepopupmenua--cdockingmanageronclosepopupmenu"></a><a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu  
 当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>备注  
 当它将要关闭当前的主窗口时，框架将发送会收到 WM_DESTROY 消息。 重写此方法以处理来自通知`CMFCPopupMenu`隶属于框架窗口中的对象时`CMFCPopupMenu`对象进程`WM_DESTROY`消息。  
  
##  <a name="a-nameonmoveminiframea--cdockingmanageronmoveminiframe"></a><a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame  
 由框架要移动的微型框架窗口调用。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFrame`  
 指向的微型框架窗口的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该方法成功。否则为`FALSE`。  
  
##  <a name="a-nameonpanecontextmenua--cdockingmanageronpanecontextmenu"></a><a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu  
 在构建一个菜单，有一个窗格的列表时，由框架调用。  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定菜单上的位置。  
  
##  <a name="a-namepanefrompointa--cdockingmanagerpanefrompoint"></a><a name="panefrompoint"></a>CDockingManager::PaneFromPoint  
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
 [in] `point`  
 指定在屏幕坐标中，若要检查该点。  
  
 [in] `nSensitivity`  
 要检查的每个窗格窗口矩形的放大量的值。 如果给定的点在此夸大区域中，一个窗格满足搜索条件。  
  
 [in] `bExactBar`  
 `TRUE`若要忽略`nSensitivity`参数; 否则为`FALSE`。  
  
 [in] `pRTCBarType`  
 如果不是`NULL`，该方法将搜索仅指定类型的窗格。  
  
 [in] `bCheckVisibility`  
 `TRUE`若要检查仅可见窗格;否则为`FALSE`。  
  
 [out] `dwAlignment`  
 如果指定点处找到一个窗格，则此参数将包含窗格中的指定点最接近的一端。 有关详细信息，请参阅“备注”部分。  
  
 [in] `pBarToIgnore`  
 如果不是`NULL`，该方法将忽略此参数指定的窗格。  
  
### <a name="return-value"></a>返回值  
 [CBasePane](../../mfc/reference/cbasepane-class.md)-派生的对象，其中包含给定的时间，或`NULL`如果不找到任何窗格。  
  
### <a name="remarks"></a>备注  
 当该函数将返回并找到一个窗格，`dwAlignment`包含指定点的对齐方式。 例如，如果该点是最接近的顶部窗格中，`dwAlignment`设置为`CBRS_ALIGN_TOP`。  
  
##  <a name="a-nameprocesspanecontextmenucommanda--cdockingmanagerprocesspanecontextmenucommand"></a><a name="processpanecontextmenucommand"></a>CDockingManager::ProcessPaneContextMenuCommand  
 由框架来选择或清除复选框为指定的命令，并重新计算布局的显示窗格中调用。  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 在菜单中的控件条 id。  
  
 [in] `nCode`  
 命令通知代码。  
  
 [in] `pExtra`  
 Void 的指针是强制转换为一个指向`CCmdUI`如果`nCode`是 CN_UPDATE_COMMAND_UI。  
  
 [in] `pHandlerInfo`  
 指向信息结构的指针。 未使用此参数。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`pEXtra`不为 NULL 和`nCode`等于 CN_UPDATE_COMMAND_UI，或如果没有具有指定的控件条`nID`。  
  
##  <a name="a-namerecalclayouta--cdockingmanagerrecalclayout"></a><a name="recalclayout"></a>CDockingManager::RecalcLayout  
 重新计算存在于列表中的控件的控件的内部布局。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bNotify`  
 未使用此参数。  
  
##  <a name="a-namereleaseemptypanecontainersa--cdockingmanagerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers  
 释放空的窗格中的容器。  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="a-nameremovehiddenmditabbedbara--cdockingmanagerremovehiddenmditabbedbar"></a><a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar  
 移除指定的栏窗格中隐藏。  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向一个图条的窗格中删除。  
  
##  <a name="a-nameremoveminiframea--cdockingmanagerremoveminiframe"></a><a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame  
 从最小的框架的列表中移除指定的范围。  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指向要删除的帧的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果指定的帧被删除;`FALSE`否则为。  
  
##  <a name="a-nameremovepanefromdockmanagera--cdockingmanagerremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager  
 注销一个窗格，并将其从列表中的扩展管理器中删除。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pWnd,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指向要删除一个窗格的指针。  
  
 [in] `bDestroy`  
 如果`TRUE`，删除窗格中被销毁。  
  
 [in] `bAdjustLayout`  
 如果`TRUE`，立即调整停靠布局。  
  
 [in] `bAutoHide`  
 如果`TRUE`，从自动隐藏栏列表中删除窗格。 如果`FALSE`，从常规窗格的列表中删除窗格。  
  
 [in] `pBarReplacement`  
 指向替换删除窗格中的窗格的指针。  
  
##  <a name="a-namereplacepanea--cdockingmanagerreplacepane"></a><a name="replacepane"></a>CDockingManager::ReplacePane  
 用一个窗格替换另一个窗格。  
  
```  
BOOL ReplacePane(
    CDockablePane* pOriginalBar,  
    CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOriginalBar`  
 指向原始窗格中的指针。  
  
 [in] `pNewBar`  
 指向替换原始窗格中的窗格中的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功替换窗格中;`FALSE`否则为。  
  
##  <a name="a-nameresortminiframesforzordera--cdockingmanagerresortminiframesforzorder"></a><a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder  
 将微型框架的列表中的帧重新排序。  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="a-namesavestatea--cdockingmanagersavestate"></a><a name="savestate"></a>CDockingManager::SaveState  
 将扩展管理器的状态保存到注册表。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 对一个注册表项路径。  
  
 [in] `uiID`  
 扩展管理器 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则已保存的状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 保存对注册表的扩展管理器的状态涉及到将保存的控件条状态、 自动隐藏条形的状态和扩展管理器中存在的最小帧的状态。  
  
##  <a name="a-namesendmessagetominiframesa--cdockingmanagersendmessagetominiframes"></a><a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames  
 将指定的消息发送到所有的微型框架。  
  
```  
BOOL SendMessageToMiniFrames(
    UINT uMessage,  
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uMessage`  
 要发送的消息。  
  
 [in] `wParam`  
 更多的消息的相关信息。  
  
 [in] `lParam`  
 更多的消息的相关信息。  
  
### <a name="return-value"></a>返回值  
 `TRUE`始终。  
  
##  <a name="a-nameserializea--cdockingmanagerserialize"></a><a name="serialize"></a>CDockingManager::Serialize  
 扩展管理器写入存档。  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in] `ar`  
 对存档对象的引用。  
  
### <a name="remarks"></a>备注  
 扩展管理器写入存档涉及到确定的停靠控件条和滑块，和写入存档的控件条、 微型框架、 自动隐藏条和 MDI 选项卡式条数。  
  
##  <a name="a-namesetautohidezordera--cdockingmanagersetautohidezorder"></a><a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder  
 设置大小、 宽度和高度的控制条和指定窗格。  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pAHDockingBar`  
 指向可停靠的窗格中的指针。  
  
##  <a name="a-namesetdockingmodea--cdockingmanagersetdockingmode"></a><a name="setdockingmode"></a>CDockingManager::SetDockingMode  
 设置停靠的模式。  
  
```  
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,  
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```  
  
### <a name="parameters"></a>参数  
 `dockMode`  
 指定新的停靠模式。 有关详细信息，请参阅“备注”部分。  
  
 `theme`  
 指定要用于智能停靠标记的主题。 它可以是下列枚举值之一︰ AFX_SDT_DEFAULT，AFX_SDT_VS2005，AFX_SDT_VS2008。  
  
### <a name="remarks"></a>备注  
 调用此静态方法，以设置停靠的模式。  
  
 `dockMode`可以是下列值之一︰  
  
- `DT_STANDARD`标准停靠模式下，当在 Visual Studio.NET 2003年中实现。 窗格拖动无需拖放的上下文中。  
  
- `DT_IMMEDIATE`在 Microsoft Visio 中实现与即时停靠模式。 窗格拖动具有拖动上下文，但会显示任何标记。  
  
- `DT_SMART`-在 Visual Studio 2005 中实现智能停靠模式。 窗格拖动具有拖动上下文，并显示智能标记来显示窗格中可以停靠位置。  
  
##  <a name="a-namesetdockstatea--cdockingmanagersetdockstate"></a><a name="setdockstate"></a>CDockingManager::SetDockState  
 设置停靠控件条、 最小的帧中，和自动隐藏条形图的状态。  
  
```  
virtual void SetDockState();
```  
  
##  <a name="a-namesetprintpreviewmodea--cdockingmanagersetprintpreviewmode"></a><a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode  
 设置的条形图的打印预览中显示打印预览模式。  
  
```  
void SetPrintPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>参数  
 [in] `bPreview`  
 `TRUE`如果打印预览模式设置;`FALSE`否则为。  
  
 [in] `pState`  
 指向预览状态的指针。 未使用此参数。  
  
##  <a name="a-namesetsmartdockingparamsa--cdockingmanagersetsmartdockingparams"></a><a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams  
 设置定义智能停靠的行为的参数。  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `params`  
 定义智能停靠的参数。  
  
### <a name="remarks"></a>备注  
 如果您想要自定义外观、 颜色或智能停靠标记的形状，请调用此方法。  
  
 若要使用智能停靠标记的默认外观，未初始化的实例传递[CSmartDockingInfo 类](../../mfc/reference/csmartdockinginfo-class.md)到`params`。  
  
##  <a name="a-nameshowdelayshowminiframesa--cdockingmanagershowdelayshowminiframes"></a><a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames  
 显示或隐藏的微型框架窗口。  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 `TRUE`若要使所示的框架的窗口处于活动状态;`FALSE to`隐藏为框架的窗口。  
  
##  <a name="a-nameshowpanesa--cdockingmanagershowpanes"></a><a name="showpanes"></a>CDockingManager::ShowPanes  
 显示或隐藏控制和自动隐藏条形图的窗格。  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 `TRUE`若要显示两个窗格;`FALSE to`隐藏窗格。  
  
### <a name="return-value"></a>返回值  
 总是为 `FALSE`。  
  
##  <a name="a-namestartsdockinga--cdockingmanagerstartsdocking"></a><a name="startsdocking"></a>CDockingManager::StartSDocking  
 启动智能停靠所指定的窗口根据智能停靠管理器的对齐方式。  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockingWnd`  
 指向要停靠窗口的指针。  
  
##  <a name="a-namestopsdockinga--cdockingmanagerstopsdocking"></a><a name="stopsdocking"></a>CDockingManager::StopSDocking  
 停止智能停靠。  
  
```  
void StopSDocking();
```  
  
##  <a name="a-namegetsmartdockingthemea--cdockingmanagergetsmartdockingtheme"></a><a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme  
 返回一个用来显示智能停靠标记的主题的静态方法。  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>返回值  
 返回下列枚举值之一︰ AFX_SDT_DEFAULT，AFX_SDT_VS2005，AFX_SDT_VS2008。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [Cframewndex 由类](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)

