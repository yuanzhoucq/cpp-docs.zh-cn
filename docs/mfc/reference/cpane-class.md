---
title: "CPane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPane
- AFXPANE/CPane
- AFXPANE/CPane::AdjustSizeImmediate
- AFXPANE/CPane::AllocElements
- AFXPANE/CPane::AllowShowOnPaneMenu
- AFXPANE/CPane::CalcAvailableSize
- AFXPANE/CPane::CalcInsideRect
- AFXPANE/CPane::CalcRecentDockedRect
- AFXPANE/CPane::CalcSize
- AFXPANE/CPane::CanBeDocked
- AFXPANE/CPane::CanBeTabbedDocument
- AFXPANE/CPane::ConvertToTabbedDocument
- AFXPANE/CPane::CopyState
- AFXPANE/CPane::Create
- AFXPANE/CPane::CreateDefaultMiniframe
- AFXPANE/CPane::CreateEx
- AFXPANE/CPane::DockByMouse
- AFXPANE/CPane::DockPane
- AFXPANE/CPane::DockPaneStandard
- AFXPANE/CPane::DockToFrameWindow
- AFXPANE/CPane::DoesAllowSiblingBars
- AFXPANE/CPane::FloatPane
- AFXPANE/CPane::GetAvailableExpandSize
- AFXPANE/CPane::GetAvailableStretchSize
- AFXPANE/CPane::GetBorders
- AFXPANE/CPane::GetClientHotSpot
- AFXPANE/CPane::GetDockSiteRow
- AFXPANE/CPane::GetExclusiveRowMode
- AFXPANE/CPane::GetHotSpot
- AFXPANE/CPane::GetMinSize
- AFXPANE/CPane::GetPaneName
- AFXPANE/CPane::GetVirtualRect
- AFXPANE/CPane::IsChangeState
- AFXPANE/CPane::IsDragMode
- AFXPANE/CPane::IsInFloatingMultiPaneFrameWnd
- AFXPANE/CPane::IsLeftOf
- AFXPANE/CPane::IsResizable
- AFXPANE/CPane::IsTabbed
- AFXPANE/CPane::LoadState
- AFXPANE/CPane::MoveByAlignment
- AFXPANE/CPane::MovePane
- AFXPANE/CPane::OnAfterChangeParent
- AFXPANE/CPane::OnBeforeChangeParent
- AFXPANE/CPane::OnPressCloseButton
- AFXPANE/CPane::OnShowControlBarMenu
- AFXPANE/CPane::OnShowControlBarMenu
- AFXPANE/CPane::RecalcLayout
- AFXPANE/CPane::SaveState
- AFXPANE/CPane::SetActiveInGroup
- AFXPANE/CPane::SetBorders
- AFXPANE/CPane::SetClientHotSpot
- AFXPANE/CPane::SetDockState
- AFXPANE/CPane::SetExclusiveRowMode
- AFXPANE/CPane::SetMiniFrameRTC
- AFXPANE/CPane::SetMinSize
- AFXPANE/CPane::SetVirtualRect
- AFXPANE/CPane::StretchPaneDeferWndPos
- AFXPANE/CPane::ToggleAutoHide
- AFXPANE/CPane::UndockPane
- AFXPANE/CPane::UpdateVirtualRect
- AFXPANE/CPane::OnAfterDock
- AFXPANE/CPane::OnAfterFloat
- AFXPANE/CPane::OnBeforeDock
- AFXPANE/CPane::OnBeforeFloat
- AFXPANE/CPane::m_bHandleMinSize
- AFXPANE/CPane::m_recentDockInfo
dev_langs:
- C++
helpviewer_keywords:
- CPane class
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: 30
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
ms.openlocfilehash: 586133277aa4a9d89ca15cdd496a1ca7e4232632
ms.lasthandoff: 02/24/2017

---
# <a name="cpane-class"></a>CPane Class
`CPane`类是增强功能[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)。 如果要升级现有 MFC 项目，则替换所有出现的`CControlBar`与`CPane`。  
  
## <a name="syntax"></a>语法  
  
```  
class CPane : public CBasePane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CPane::~CPane`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新计算一个窗格的布局。|  
|[CPane::AllocElements](#allocelements)|分配存储供内部使用。|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|指定是否在运行时生成的应用程序的窗格列表中列出窗格。|  
|[CPane::CalcAvailableSize](#calcavailablesize)|计算大小中指定的矩形和当前窗口矩形之间的差异。|  
|[CPane::CalcInsideRect](#calcinsiderect)|计算内部的窗格中，并考虑边框和控制手柄的矩形。|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|计算最近停靠的矩形。|  
|[CPane::CalcSize](#calcsize)|计算窗格中的大小。|  
|[CPane::CanBeDocked](#canbedocked)|确定是否可以在指定的基窗格停靠窗格。|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|确定是否可将窗格中转换选项卡式文档。|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|转换选项卡式文档停靠窗格。|  
|[CPane::CopyState](#copystate)|将复制一个窗格的状态。 (重写[CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate)。)|  
|[CPane::Create](#create)|创建的控件条，并将其附加到`CPane`对象。|  
|[CPane::CreateDefaultMiniframe](#createdefaultminiframe)|创建浮动窗格的微型框架窗口。|  
|[CPane::CreateEx](#createex)|创建的控件条，并将其附加到`CPane`对象。|  
|`CPane::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CPane::DockByMouse](#dockbymouse)|通过使用鼠标停靠方法停靠窗格。|  
|[CPane::DockPane](#dockpane)|浮动窗格停靠到基窗格中。|  
|[CPane::DockPaneStandard](#dockpanestandard)|通过使用大纲 （标准） 停靠停靠窗格。|  
|[CPane::DockToFrameWindow](#docktoframewindow)|可停靠窗格停靠到的帧中。 （重写 `CBasePane::DockToFrameWindow`。）|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|指示是否可以将停靠在同一行中当前窗格中的停靠位置的另一个窗格。|  
|[CPane::FloatPane](#floatpane)|浮动窗格。|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|返回所需量，以像素为单位，可以展开窗格。|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|返回所需量，以像素为单位，可以收缩窗格。|  
|[CPane::GetBorders](#getborders)|返回窗格中的边框的宽度。|  
|[CPane::GetClientHotSpot](#getclienthotspot)|返回*热点*为窗格。|  
|[CPane::GetDockSiteRow](#getdocksiterow)|返回在其中停靠窗格的停靠行。|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|确定是否在排他行模式下为窗格。|  
|[CPane::GetHotSpot](#gethotspot)|返回存储在基础的热点`CMFCDragFrameImpl`对象。|  
|[CPane::GetMinSize](#getminsize)|检索允许大小为窗格中的最小。|  
|[CPane::GetPaneName](#getpanename)|检索窗格中的标题。|  
|`CPane::GetResizeStep`|在内部使用。|  
|`CPane::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CPane::GetVirtualRect](#getvirtualrect)|检索*虚拟矩形*的窗格。|  
|[CPane::IsChangeState](#ischangestate)|移动窗格中时，此方法分析相对于其他窗格、 停靠行和微型框架窗口窗格中的位置，并返回相应`AFX_CS_STATUS`值。|  
|[CPane::IsDragMode](#isdragmode)|指定是否进行拖动窗格。|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定是否在多窗格框架窗口中为窗格。 （重写 `CBasePane::IsInFloatingMultiPaneFrameWnd`。）|  
|[CPane::IsLeftOf](#isleftof)|确定的 （或更高版本） 是否保持为窗格中指定的矩形。|  
|[CPane::IsResizable](#isresizable)|确定是否可以调整大小窗格。 (重写[cbasepane:: Isresizable](../../mfc/reference/cbasepane-class.md#isresizable)。)|  
|[CPane::IsTabbed](#istabbed)|确定是否已在选项卡式窗口选项卡控件中插入窗格。 (重写[CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed)。)|  
|[CPane::LoadState](#loadstate)|从注册表加载的窗格中的状态。 (重写[CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate)。)|  
|[CPane::MoveByAlignment](#movebyalignment)|将窗格中的虚拟矩形移动按指定的数量。|  
|[CPane::MovePane](#movepane)|将窗格中移动到指定的矩形。|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|当一个窗格的父级发生更改时由框架调用。|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|在窗格中的父级是将要发生更改时由框架调用。|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|当用户选择关闭按钮上的窗格中的标题由框架调用。|  
|`CPane::OnProcessDblClk`|在内部使用。|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。|  
|`CPane::PrepareToDock`|在内部使用。|  
|[CPane::RecalcLayout](#recalclayout)|重新计算窗格中的布局信息。 (重写[CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout)。)|  
|[CPane::SaveState](#savestate)|将窗格中的状态保存到注册表。 (重写[CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate)。)|  
|[CPane::SetActiveInGroup](#setactiveingroup)|标记为活动的窗格。|  
|[CPane::SetBorders](#setborders)|设置窗格中的边框值。|  
|[CPane::SetClientHotSpot](#setclienthotspot)|设置窗格中作用点。|  
|[CPane::SetDockState](#setdockstate)|还原停靠窗格中的状态信息。|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|启用或禁用的排他行模式。|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|设置默认微型框架窗口的运行时类信息。|  
|[CPane::SetMinSize](#setminsize)|设置允许为窗格中的大小的最小。|  
|[CPane::SetVirtualRect](#setvirtualrect)|集*虚拟矩形*的窗格。|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|拉伸垂直或水平基于的停靠样式窗格。|  
|[CPane::ToggleAutoHide](#toggleautohide)|切换自动隐藏模式。|  
|[CPane::UndockPane](#undockpane)|从停靠站点、 默认滑块或当前停靠位置的微型框架窗口中删除窗格。 (重写[CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane)。)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|更新的虚拟矩形。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|由框架调用时已停靠窗格。|  
|[CPane::OnAfterFloat](#onafterfloat)|浮动窗格时由框架调用。|  
|[CPane::OnBeforeDock](#onbeforedock)|即将停靠窗格时，由框架调用。|  
|[CPane::OnBeforeFloat](#onbeforefloat)|要浮动窗格时，由框架调用。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|启用最小大小的窗格的一致处理。|  
|[CPane::m_recentDockInfo](#m_recentdockinfo)|包含新的停靠信息。|  
  
## <a name="remarks"></a>备注  
 通常情况下，`CPane`不直接实例化对象。 如果您需要具有停靠功能窗格中，派生您的对象从[CDockablePane](../../mfc/reference/cdockablepane-class.md)。 如果您需要工具栏功能，派生您的对象从[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)。  
  
 当您从派生类`CPane`，可在停靠[CDockSite](../../mfc/reference/cdocksite-class.md) ，它可以浮动在[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxPane.h  
  
##  <a name="adjustsizeimmediate"></a>CPane::AdjustSizeImmediate  
 立即重新计算一个窗格的布局。  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bRecalcLayout`  
 `TRUE`若要自动重新计算窗格中; 的布局否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法时动态地更改窗格的布局。 例如，您可能想要隐藏或显示工具栏按钮时调用此方法。  
  
##  <a name="allocelements"></a>CPane::AllocElements  
 分配存储供内部使用。  
  
```  
BOOL AllocElements(
    int nElements,  
    int cbElement);
```  
  
### <a name="parameters"></a>参数  
 [in] `nElements`  
 为其分配存储的元素数。  
  
 [in] `cbElement`  
 大小 （以字节为单位的元素）。  
  
### <a name="return-value"></a>返回值  
 `FALSE`如果内存分配失败;否则为`TRUE`。  
  
##  <a name="allowshowonpanemenu"></a>CPane::AllowShowOnPaneMenu  
 指定是否在运行时生成的应用程序的窗格列表中列出窗格。  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中会显示在列表中;否则为`FALSE`。 基实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 应用程序向导生成的应用程序包含菜单选项，其中列出了它所包含的窗格。 此方法确定是否在列表中显示窗格。  
  
##  <a name="calcavailablesize"></a>CPane::CalcAvailableSize  
 计算大小中指定的矩形和当前窗口矩形之间的差异。  
  
```  
virtual CSize CalcAvailableSize(CRect rectRequired);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectRequired`  
 所需的矩形。  
  
### <a name="return-value"></a>返回值  
 宽度和高度之间的差异`rectRequired`和当前窗口矩形。  
  
##  <a name="calcinsiderect"></a>CPane::CalcInsideRect  
 计算内部的窗格中，包括边框和控制手柄的矩形。  
  
```  
void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rect`  
 包含的大小和偏移量窗格中的工作区。  
  
 [in] `bHorz`  
 `TRUE`如果窗格中将采用水平; 方向否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 它在必须重新计算窗格布局时，将由框架调用此方法。 `rect`参数填充的大小和偏移量窗格中的工作区。 这包括其边框和控制手柄。  
  
##  <a name="calcrecentdockedrect"></a>CPane::CalcRecentDockedRect  
 计算最近停靠的矩形。  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>备注  
 此方法将更新[CPane::m_recentDockInfo](#m_recentdockinfo)。  
  
##  <a name="calcsize"></a>CPane::CalcSize  
 计算窗格中的大小。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>参数  
 [in] `bVertDock`  
 `TRUE`如果要垂直停靠窗格中`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 此方法的默认实现返回的大小为 （0，0）。  
  
### <a name="remarks"></a>备注  
 派生的类应重写此方法。  
  
##  <a name="canbedocked"></a>CPane::CanBeDocked  
 确定是否可以在指定的基窗格停靠窗格。  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 指定可停靠此窗格中的位置窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在指定的停靠窗格; 可以停靠此窗格，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法通常称为框架可确定是否可以在指定的停靠窗格停靠窗格。 若要确定是否可以停靠窗格中，该方法的计算结果窗格中的当前启用停靠的对齐方式。  
  
 然后可以通过调用停靠到框架窗口的各个边[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="canbetabbeddocument"></a>CPane::CanBeTabbedDocument  
 确定是否可以将窗格中转换到选项卡式文档。  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以转换到选项卡式文档中。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类中的，并返回`FALSE`如果您想要防止一个窗格被转换到选项卡式文档。 选项卡式的文档不会列出在窗口的位置菜单中。  
  
##  <a name="converttotabbeddocument"></a>CPane::ConvertToTabbedDocument  
 转换选项卡式文档停靠窗格。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActiveTabOnly`  
 中没有使用`CPane::ConvertToTabbedDocument`。  
  
### <a name="remarks"></a>备注  
 仅可停靠窗格可以转换为选项卡式文档。 有关信息，请参阅[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。  
  
##  <a name="copystate"></a>CPane::CopyState  
 将复制一个窗格的状态。  
  
```  
virtual void CopyState(CPane* pOrgBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOrgBar`  
 指向一个窗格的指针。  
  
### <a name="remarks"></a>备注  
 此方法将复制的状态`pOrgBar`到当前窗格中。  
  
##  <a name="create"></a>CPane::Create  
 创建的控件条，并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszClassName`  
 指定的 Windows 类的名称。  
  
 [in] `dwStyle`  
 指定的窗口样式特性。 有关详细信息，请参阅[窗口样式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和位置`pParentWnd`窗口中的，在工作区坐标。  
  
 [in][out]`pParentWnd`  
 指定此窗格中的父窗口。  
  
 [in] `nID`  
 指定窗格中的 ID。  
  
 [in] `dwControlBarStyle`  
 指定窗格中的样式。 有关详细信息，请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。  
  
 [in][out]`pContext`  
 指定窗格中的创建上下文。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建窗格中否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法创建一个窗口窗格并将其附加到`CPane`对象。  
  
 如果显式未初始化[CPane::m_recentDockInfo](#m_recentdockinfo)之前调用`Create`，该参数`rect`将用作该矩形时浮动或停靠窗格。  
  
##  <a name="createdefaultminiframe"></a>CPane::CreateDefaultMiniframe  
 创建浮动窗格的微型框架窗口。  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectInitial`  
 指定的初始大小和要创建的微型框架窗口的位置，在屏幕坐标。  
  
### <a name="return-value"></a>返回值  
 新创建的微型框架窗口中。  
  
### <a name="remarks"></a>备注  
 通过浮动窗格中时创建的微型框架窗口的框架调用此方法。 微型框架窗口可以是类型[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)或类型[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)。 窗格中是否创建了多微型框架窗口`AFX_CBRS_FLOAT_MULTI`样式。  
  
 微型框架窗口的运行时类信息存储在`CPane::m_pMiniFrameRTC`成员。 派生的类可用于将此成员的设置，如果您决定创建自定义的微型框架窗口。  
  
##  <a name="createex"></a>CPane::CreateEx  
 创建的控件条，并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwStyleEx`  
 指定扩展的窗口样式特性。 有关详细信息，请参阅[扩展窗口样式](../../mfc/reference/extended-window-styles.md)。  
  
 [in] `lpszClassName`  
 指定的 Windows 类的名称。  
  
 [in] `dwStyle`  
 指定窗口的样式特性。 有关详细信息，请参阅[窗口样式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和位置`pParentWnd`窗口中的，在工作区坐标。  
  
 [in][out]`pParentWnd`  
 指定此窗格中的父窗口。  
  
 [in] `nID`  
 指定窗格中的 ID。  
  
 [in] `dwControlBarStyle`  
 指定窗格中的样式。 有关详细信息，请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。  
  
 [in][out]`pContext`  
 指定窗格中的创建上下文。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建窗格中否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法创建一个窗口窗格并将其附加到`CPane`对象。  
  
 如果显式未初始化[CPane::m_recentDockInfo](#m_recentdockinfo)之前调用`CreateEx`，该参数`rect`将用作该矩形时浮动或停靠窗格。  
  
##  <a name="dockbymouse"></a>CPane::DockByMouse  
 通过使用鼠标停靠窗格。  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 指定要与其进行停靠此窗格中基本窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠窗格，否则为`FALSE`。  
  
##  <a name="dockpane"></a>CPane::DockPane  
 浮动窗格停靠到基窗格中。  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pDockBar`  
 指定基本窗格以停靠此窗格。  
  
 [in] `lpRect`  
 在此窗格的停靠位置基本窗格中指定的矩形。  
  
 [in] `dockMethod`  
 指定要使用的扩展方法。 可用选项如下所示︰  
  
|选项|描述|  
|------------|-----------------|  
|`DM_UNKNOWN`|未知的停靠方法时，框架将使用此选项。 窗格中不存储其最新的浮动位置。 此选项还可用于以编程方式将窗格停靠时不需要存储的最新的浮动位置。|  
|`DM_MOUSE`|在内部使用。|  
|`DM_DBL_CLICK`|双击控制手柄时使用此选项。 在其最新的停靠位置重新定位窗格。 如果窗格中通过双击取消停靠，窗格中重新定位在其最新的浮动位置。|  
|`DM_SHOW`|此选项可用于以编程方式将窗格停靠。 窗格中存储其最新的浮动位置。|  
|`DM_RECT`|在由指定的区域停靠窗格`lpRect`。|  
|`DM_STANDARD`|当使用此选项时，框架绘制为大纲框架窗格中，在移动时。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠窗格，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法将窗格停靠到基本窗格中所指定的`pDockBar`参数。 您必须首先启用通过调用停靠[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="dockpanestandard"></a>CPane::DockPaneStandard  
 通过使用大纲 （标准） 停靠停靠窗格。  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>参数  
 [in] `bWasDocked`  
 `TRUE`如果成功停靠窗格中;，否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 此方法始终返回`this`指针。  
  
### <a name="remarks"></a>备注  
 此方法仅用于派生自的窗格[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。 有关详细信息，请参阅[CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard)。  
  
##  <a name="docktoframewindow"></a>CPane::DockToFrameWindow  
 可停靠窗格停靠到的帧中。  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 您希望将停靠到窗格中的父框架的一端。  
  
 [in] `lpRect`  
 指定的大小。  
  
 [in] `dwDockFlags`  
 已忽略。  
  
 [in] `pRelativeBar`  
 已忽略。  
  
 [in] `nRelativeIndex`  
 已忽略。  
  
 [in] `bOuterEdge`  
 如果`TRUE`还有其他可停靠窗格在指定的一侧`dwAlignment`，在其他窗格，请外停靠窗格中更接近于父框架的边缘。 如果`FALSE`，窗格中更接近停靠到客户端区域的中心。  
  
### <a name="return-value"></a>返回值  
 `FALSE`如果窗格分隔符 ( [CPaneDivider 类](../../mfc/reference/cpanedivider-class.md)) 创建; 否则为不能为`TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="doesallowsiblingbars"></a>CPane::DoesAllowSiblingBars  
 指示是否可以将停靠在同一行中当前窗格中的停靠位置的另一个窗格。  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此窗格可以停靠到另一个窗格与自身; 同一行上否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 您可以通过启用或禁用此行为调用[CPane::SetExclusiveRowMode](#setexclusiverowmode)。  
  
 默认情况下，工具栏具有排他行模式被禁用，菜单栏有启用的排他行模式。  
  
##  <a name="floatpane"></a>CPane::FloatPane  
 浮动窗格。  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod = DM_UNKNOWN,  
    bool bShow = true);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectFloat`  
 在屏幕坐标中，定位窗格浮动时指定的位置。  
  
 [in] `dockMethod`  
 指定要在浮动窗格中时使用的停靠方法。 有关可能的值的列表，请参阅[CPane::DockPane](#dockpane)。  
  
 [in] `bShow`  
 `TRUE`若要显示窗格时浮动;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功浮动窗格中，或者不能浮动窗格中，因为[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)返回`FALSE`; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以浮动中由指定的位置窗格中`rectFloat`参数。 此方法会自动创建窗格中的父微型框架窗口。  
  
##  <a name="getavailableexpandsize"></a>CPane::GetAvailableExpandSize  
 返回所需量，以像素为单位，可以展开窗格。  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果为水平停靠窗格中，返回值是可用的宽度;否则，返回值是可用的高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getavailablestretchsize"></a>CPane::GetAvailableStretchSize  
 返回所需量，以像素为单位，可以收缩窗格。  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位，窗格中可以收缩的量。 如果水平停靠窗格中，此量的可用宽度。否则，它是可用的高度。  
  
### <a name="remarks"></a>备注  
 可用扩展的大小减去计算得出允许大小为窗格中的最小 ( [CPane::GetMinSize](#getminsize)) 中的当前大小 ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect))。  
  
##  <a name="getborders"></a>CPane::GetBorders  
 返回窗格中的边框的宽度。  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含的当前宽度，以像素为单位的窗格中每一侧。 例如，值为`left`的成员`CRect`对象是左边框的宽度。  
  
### <a name="remarks"></a>备注  
 若要设置边框的大小，请调用[CPane::SetBorders](#setborders)。  
  
##  <a name="getclienthotspot"></a>CPane::GetClientHotSpot  
 返回*热点*为窗格。  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 *热点*是在窗格中，以用户选择和包含要移动窗格中的点。 窗格中移动从停靠位置时，作用点用于流畅的动画。  
  
##  <a name="getdocksiterow"></a>CPane::GetDockSiteRow  
 返回停靠的行 ( [CDockingPanesRow 类](../../mfc/reference/cdockingpanesrow-class.md)) 中停靠窗格。  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CDockingPanesRow`*，它指向停靠窗格的停靠行或`NULL`如果未停靠窗格。  
  
##  <a name="getexclusiverowmode"></a>CPane::GetExclusiveRowMode  
 确定是否在排他行模式下为窗格。  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中的排他行模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 有关排他行模式的详细信息，请参阅[CPane::SetExclusiveRowMode](#setexclusiverowmode)。  
  
##  <a name="gethotspot"></a>CPane::GetHotSpot  
 返回存储在基础的热点`CMFCDragFrameImpl`对象。  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 `CPane`类包含`CMFCDragFrameImpl`对象， `m_dragFrameImpl`，即负责绘制当用户在标准停靠模式下移动一个窗格显示的矩形。 作用点用于绘制矩形相对于当前的鼠标位置，当用户移动窗格。  
  
##  <a name="getminsize"></a>CPane::GetMinSize  
 检索允许大小为窗格中的最小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `size`  
 一个`CSize`用允许的大小的最小填充的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpanename"></a>CPane::GetPaneName  
 检索窗格中的标题。  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `strName`  
 一个`CString`使用的标题名称填充的对象。  
  
### <a name="remarks"></a>备注  
 停靠或浮动窗格时，会将该窗格标题显示在标题区域中。 如果窗格中的选项卡式组的一部分，标题会显示在选项卡区域中。 如果在自动隐藏模式下窗格中，将标题显示在`CMFCAutoHideButton`。  
  
##  <a name="getvirtualrect"></a>CPane::GetVirtualRect  
 检索*虚拟矩形*的窗格。  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectVirtual`  
 一个`CRect`用的虚拟矩形填充的对象。  
  
### <a name="remarks"></a>备注  
 窗格中移动时，框架会将窗格中的原始位置存储在虚拟的矩形中。 则框架可使用的虚拟矩形还原窗格中的原始位置。  
  
 请勿调用方法，除非要以编程方式移动窗格相关的虚拟矩形。  
  
##  <a name="ischangestate"></a>CPane::IsChangeState  
 移动窗格中时，此方法将分析其位置相对于其他窗格、 停靠行和最小化框架窗口，并返回相应`AFX_CS_STATUS`值。  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nOffset`  
 指定停靠区分大小写。 例如，一个窗格，其中内移动时，`nOffset`将停靠停靠行中的像素为单位。  
  
 [in] `ppTargetBar`  
 方法返回时，`ppTargetBar`包含任一一个向其应停靠当前窗格中，该对象的指针或`NULL`是否应进行未停靠。  
  
### <a name="return-value"></a>返回值  
 以下项之一`AFX_CS_STATUS`值︰  
  
|值|说明|  
|-----------|-----------------|  
|`CS_NOTHING`|在停靠站点附近不是窗格。 框架将窗格未停靠。|  
|`CS_DOCK_IMMEDIATELY`|在窗格中，在停靠站点，与`DT_IMMEDIATE`启用样式。 框架立即停靠窗格。|  
|`CS_DELAY_DOCK`|在窗格中，在停靠站点的另一个的停靠窗格或边缘的主框架。 当用户释放移动，框架将停靠窗格。|  
|`CS_DELAY_DOCK_TO_TAB`|在窗格中，通过使选项卡式窗口中停靠窗格的停靠站点。 在窗格中，通过另一个的停靠窗格的标题或通过选项卡式窗格中的选项卡区域时，将发生这种情况。 当用户释放移动，框架将停靠窗格。|  
  
##  <a name="isdragmode"></a>CPane::IsDragMode  
 指定是否在移动窗格。  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果正在移动窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CPane::IsInFloatingMultiPaneFrameWnd  
 指定是否在多窗格框架窗口中为窗格中 ( [CMultiPaneFrameWnd 类](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中处于多窗格框架窗口。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 仅可停靠窗格可以浮动在多窗格框架窗口中。 因此，`CPane::IsInFloatingMultiPaneFrameWnd`始终返回`FALSE`。  
  
##  <a name="isleftof"></a>CPane::IsLeftOf  
 确定的 （或更高版本） 是否保持为窗格中指定的矩形。  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 一个`CRect`用于比较的对象。  
  
 [in] `bWindowRect`  
 如果`TRUE`，`rect`被假定为包含屏幕坐标; 如果`FALSE`，`rect`假定为包含工作区坐标。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 如果水平停靠窗格中，此方法检查是否保持其位置的`rect`。 否则，此方法检查该位置是否高于`rect`。  
  
##  <a name="isresizable"></a>CPane::IsResizable  
 指定是否可以窗格中的大小。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在窗格中，可调整大小;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 基本`CPane`对象不是可调整大小。  
  
 停靠管理器使用可调整大小的标志来决定窗格中的布局。 非可调整大小窗格位于始终与父框架的外边缘。  
  
 非可调整大小窗格不能驻留在停靠容器。  
  
##  <a name="istabbed"></a>CPane::IsTabbed  
 确定是否已被窗格中插入的选项卡式窗口选项卡控件。  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中选项卡式;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 选项卡式的状态将单独处理从浮动、 停靠，和自动隐藏状态。  
  
##  <a name="loadstate"></a>CPane::LoadState  
 从注册表加载的窗格中的状态。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 配置文件名称。  
  
 [in] `nIndex`  
 配置文件的索引。  
  
 [in] `uiID`  
 窗格 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则加载窗格状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以从注册表加载的窗格中的状态。 在保存的要加载的其他信息的派生类中重写它[CPane::SaveState](#savestate)。  
  
 当重写此方法时，还调用基方法，并返回`FALSE`如果基方法所返回`FALSE`。  
  
##  <a name="m_bhandleminsize"></a>CPane::m_bHandleMinSize  
 允许最小窗格大小一致的处理。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>备注  
 如果应用程序中的一个或多个停靠窗格重写`GetMinSize`，或如果您的应用程序调用`SetMinSize`，您可能想要将此静态成员设置为`TRUE`为了使框架可以一致地处理窗格大小的方式。  
  
 如果此值设置为`TRUE`，所有窗格应低于其最小大小减小其大小将被都剪裁，未拉伸。 因为 framework 将窗口区域用于窗格大小调整用途，不会更改为停靠窗格，如果此值设置为的窗口区域的大小`TRUE`。  
  
##  <a name="m_recentdockinfo"></a>CPane::m_recentDockInfo  
 包含新的停靠信息。  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>备注  
 框架将窗格中的最新停靠状态信息存储在此成员。  
  
##  <a name="movebyalignment"></a>CPane::MoveByAlignment  
 将窗格中的虚拟矩形移动按指定的数量。  
  
```  
BOOL MoveByAlignment(
    DWORD dwAlignment,  
    int nOffset);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定窗格中的对齐方式。  
  
 [in] `nOffset`  
 以像素为单位，要移动的窗格和虚拟矩形量。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 `dwAlignment`可以是下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|启用可停靠在顶部的框架窗口的工作区窗格。|  
|`CBRS_ALIGN_BOTTOM`|启用要停靠到框架窗口的工作区的底部窗格。|  
|`CBRS_ALIGN_LEFT`|启用要停靠到框架窗口的工作区的左侧窗格。|  
|`CBRS_ALIGN_RIGHT`|启用可停靠到右侧的框架窗口的工作区窗格。|  
|`CBRS_ALIGN_ANY`|启用可停靠到任何一侧的框架窗口的工作区窗格。|  
  
 如果`dwAlignment`包含`CBRS_ALIGN_LEFT`或`CBRS_ALIGN_RIGHT`标志、 窗格和虚拟矩形移水平; 否则为如果`dwAlignment`包含`CBRS_ALIGN_TOP`或`CBRS_ALIGN_BOTTOM`垂直移动标志、 窗格和虚拟的矩形。  
  
##  <a name="movepane"></a>CPane::MovePane  
 将窗格中移动到指定的矩形。  
  
```  
virtual CSize MovePane(
    CRect rectNew,  
    BOOL bForceMove,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectNew`  
 指定窗格中的新矩形。  
  
 [in] `bForceMove`  
 如果`TRUE`，此方法将忽略的最小允许的窗格大小 ( [CPane::GetMinSize](#getminsize)); 否则为为窗格中会进行调整，如有必要，以确保它至少可以允许大小的最小。  
  
 [in] `hdwp`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 一个`CSize`对象，其中包含新、 旧矩形之间的差异的宽度和高度 (旧矩形 – `rectNew`)。  
  
### <a name="remarks"></a>备注  
 此方法仅用于可停靠窗格。  
  
##  <a name="onafterchangeparent"></a>CPane::OnAfterChangeParent  
 当一个窗格的父级发生更改时由框架调用。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pWndOldParent`  
 窗格中的上一个父窗口。  
  
### <a name="remarks"></a>备注  
 由于停靠或浮动状态操作已更改的父级的一个窗格时，将由框架调用此方法。  
  
##  <a name="onafterdock"></a>CPane::OnAfterDock  
 由框架调用时已停靠窗格。  
  
```  
virtual void OnAfterDock(
    CBasePane* pBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 未使用此参数。  
  
 [in] `lpRect`  
 未使用此参数。  
  
 [in] `dockMethod`  
 未使用此参数。  
  
##  <a name="onafterfloat"></a>CPane::OnAfterFloat  
 由框架调用后一个窗格浮动。  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>备注  
 如果您想要执行任何处理后一个窗格浮动,，可以重写此方法在派生类中。  
  
##  <a name="onbeforechangeparent"></a>CPane::OnBeforeChangeParent  
 在窗格中的父级是将要发生更改时由框架调用。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pWndNewParent`  
 指定新的父窗口。  
  
 [in] `bDelay`  
 `TRUE`若要延迟停靠布局的全局调整;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 由框架调用此方法，将要更改，因为正在窗格中窗格中的父级时停靠或浮动。  
  
 默认情况下，窗格中已取消注册与停靠窗格中通过调用`CDockSite::RemovePane`。  
  
##  <a name="onbeforedock"></a>CPane::OnBeforeDock  
 要停靠窗格时，由框架调用。  
  
```  
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`ppDockBar`  
 指定到停靠此窗格中的窗格。  
  
 [in] `lpRect`  
 指定的插接矩形。  
  
 [in] `dockMethod`  
 指定的扩展方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以停靠窗格。 如果该函数将返回`FALSE`，停靠的操作将被中止。  
  
### <a name="remarks"></a>备注  
 即将停靠窗格时，将由框架调用此方法。 如果您想要执行任何处理之前最后停靠窗格中，可以重写此方法在派生类中。  
  
##  <a name="onbeforefloat"></a>CPane::OnBeforeFloat  
 当一个窗格处于有关为浮点数，由框架调用。  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectFloat`  
 当处于浮动状态时指定的位置和大小窗格。  
  
 [in] `dockMethod`  
 指定窗格中的扩展方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以浮动窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当一个窗格处于有关为浮点数，由框架调用此方法。 如果您想要执行任何处理之前最后浮动窗格中，可以重写此方法在派生类中。  
  
##  <a name="onpressclosebutton"></a>CPane::OnPressCloseButton  
 当用户按关闭按钮上的窗格中的标题由框架调用。  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>备注  
 由框架调用此方法，当用户按下**关闭**窗格的标题上的按钮。 若要接收有关其通知**关闭**事件，您可以重写此方法在派生类中的。  
  
##  <a name="onshowcontrolbarmenu"></a>CPane::OnShowControlBarMenu  
 当即将显示特殊窗格菜单时由框架调用。  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定菜单位置。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以显示菜单;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 菜单包含多个项，使您能够指定窗格中的行为，即︰**浮动**，**停靠**，**自动隐藏**，和**隐藏**。 您可以通过调用启用所有窗格在此菜单[CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu)。  
  
##  <a name="recalclayout"></a>CPane::RecalcLayout  
 重新计算窗格中的布局信息。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 如果停靠窗格中，此方法通过将其大小设置为窗格中的当前大小更新窗格中的虚拟矩形。  
  
 如果浮动的窗格中，此方法通知父级最小化框架可调整大小的最小化帧大小的窗格。 框架将确保最小化帧至少已允许窗格中的大小的最小 ( [CPane::GetMinSize](#getminsize)) 并调整其大小最小化框架，如有必要。  
  
##  <a name="savestate"></a>CPane::SaveState  
 将窗格中的状态保存到注册表。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 配置文件名称。  
  
 [in] `nIndex`  
 配置文件的索引。  
  
 [in] `uiID`  
 窗格 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则已保存的状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在窗格中的状态保存到注册表时，框架将调用此方法。 重写`SaveState`在派生类可存储附加信息。  
  
 当重写此方法时，还调用基方法，并返回`FALSE`如果基方法所返回`FALSE`。  
  
##  <a name="setactiveingroup"></a>CPane::SetActiveInGroup  
 标记为活动的窗格。  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActive`  
 一个`BOOL`，它指定是否窗格中会被标记为活动状态。  
  
### <a name="remarks"></a>备注  
 当显示可停靠窗格或选择一个自动隐藏按钮时，相应的自动隐藏窗格中标记为活动。  
  
 程序与窗格中的自动隐藏按钮的外观取决于两个因素。 如果窗格中处于活动状态，并且`static``BOOL``CMFCAutoHideButton::m_bOverlappingTabs`是`TRUE`，框架将自动隐藏按钮显示为图标和标签。 对于处于非活动状态的窗格中，框架显示自动隐藏图标。  
  
 如果`CMFCAutoHideButton::m_bOverlappingTabs`是`FALSE`，或者如果窗格中不在组中，框架将显示一个图标和标签相关联的自动隐藏按钮。  
  
##  <a name="setborders"></a>CPane::SetBorders  
 设置窗格中的边框值。  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 [in] `cxLeft`  
 指定以像素为单位，窗格中的左边框的宽度。  
  
 [in] `cyTop`  
 指定以像素为单位窗格中的上边框的宽度。  
  
 [in] `cxRight`  
 指定以像素为单位窗格中的右边框的宽度。  
  
 [in] `cyBottom`  
 指定以像素为单位窗格中的下边框的宽度。  
  
 [in] `lpRect`  
 一个[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含以像素为单位的窗格中的每个边框的宽度。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置窗格中的边框的大小。  
  
##  <a name="setclienthotspot"></a>CPane::SetClientHotSpot  
 集*热点*为窗格。  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `ptNew`  
 一个`CPoint`对象，它指定新的作用点。  
  
### <a name="remarks"></a>备注  
 *热点*是在窗格中，以用户选择和包含要移动窗格中的点。 作用点用于固定位置中的窗格中拖动时流畅的动画。  
  
##  <a name="setdockstate"></a>CPane::SetDockState  
 还原停靠窗格中的状态信息。  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockManager`  
 指向主框架窗口的扩展管理器的指针。  
  
### <a name="remarks"></a>备注  
 此方法是由框架调用以还原窗格中的最近插接状态信息。 一个窗格最近插接状态将信息存储在[CPane::m_recentDockInfo](#m_recentdockinfo)。 有关详细信息，请参阅[CRecentDockSiteInfo 类](../../mfc/reference/crecentdocksiteinfo-class.md)。  
  
 此外可以调用此方法以设置的插接状态时从外部源加载窗格中的信息。  
  
##  <a name="setexclusiverowmode"></a>CPane::SetExclusiveRowMode  
 启用或禁用的排他行模式。  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bExclusive`  
 `TRUE`若要启用排他行模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以启用或禁用排他行模式。 排他行模式下一个窗格时，它不能与任何其他工具栏共享同一行。  
  
 默认情况下，所有工具栏都具有排他行模式被禁用，菜单栏有启用的排他行模式。  
  
##  <a name="setminsize"></a>CPane::SetMinSize  
 设置允许为窗格中的大小的最小。  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>参数  
 [in] `size`  
 一个`CSize`对象，其中包含允许大小为窗格中的最小。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setvirtualrect"></a>CPane::SetVirtualRect  
 集*虚拟矩形*的窗格。  
  
```  
void SetVirtualRect(
    const CRect& rect,  
    BOOL bMapToParent = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 一个`CRect`对象，它指定要设置的虚拟矩形。  
  
 [in] `bMapToParent`  
 指定`TRUE`如果`rect`包含相对于父窗口的点。  
  
### <a name="remarks"></a>备注  
 一个*虚拟矩形*移动时，将存储一个窗格的原始位置。 则框架可使用的虚拟矩形来还原到原始位置。  
  
 请勿调用方法，除非要以编程方式移动窗格相关的虚拟矩形。  
  
##  <a name="setminiframertc"></a>CPane::SetMiniFrameRTC  
 设置默认微型框架窗口的运行时类信息。  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pClass`  
 指定最小化框架窗口的运行时类信息。  
  
### <a name="remarks"></a>备注  
 浮动窗格中，将其放置[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) （最小化框架） 窗口。 您可以提供自定义`CPaneFrameWnd`-派生的类将成为时使用[CPane::CreateDefaultMiniframe](#createdefaultminiframe)调用。  
  
##  <a name="stretchpanedeferwndpos"></a>CPane::StretchPaneDeferWndPos  
 拉伸垂直或水平基于的停靠样式窗格。  
  
```  
virtual int StretchPaneDeferWndPos(
    int nStretchSize,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>参数  
 [in] `nStretchSize`  
 金额，以像素为单位，以便进行拉伸窗格。 使用负值收缩窗格。  
  
 [in] `hdwp`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 实际的量，以像素为单位，已扩展窗格。  
  
### <a name="remarks"></a>备注  
 如果有必要，此方法修改`nStretchSize`以确保窗格中不会超过大小限制。 这些限制可通过调用获取[CPane::GetAvailableStretchSize](#getavailablestretchsize)和[CPane::GetAvailableExpandSize](#getavailableexpandsize)。  
  
##  <a name="toggleautohide"></a>CPane::ToggleAutoHide  
 切换自动隐藏模式。  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>备注  
 调用此方法来切换自动隐藏模式。 若要切换到自动隐藏模式，必须到主框架窗口停靠窗格。  
  
##  <a name="undockpane"></a>CPane::UndockPane  
 从停靠站点、 默认滑块或当前停靠位置的微型框架窗口中删除窗格。  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDelay`  
 如果`FALSE`，框架将调用[cbasepane:: Adjustdockinglayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)若要调整停靠布局。  
  
### <a name="remarks"></a>备注  
 使用此方法以编程方式取消停靠窗格。  
  
##  <a name="updatevirtualrect"></a>CPane::UpdateVirtualRect  
 更新的虚拟矩形。  
  
```  
void UpdateVirtualRect();  
void UpdateVirtualRect(CPoint ptOffset);  
  void UpdateVirtualRect(CSize sizeNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `ptOffset`  
 一个`CPoint`对象，它指定按其轮换窗格中的偏移量。  
  
 [in] `sizeNew`  
 一个`CSize`对象，它指定窗格中的新大小。  
  
### <a name="remarks"></a>备注  
 第一个重载使用当前的位置和窗格的大小按设置的虚拟矩形。  
  
 第二个重载将由指定的金额右移的虚拟矩形`ptOffset`。  
  
 第三个重载使用窗格和由指定的大小的当前位置设置的虚拟矩形`sizeNew`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CBasePane 类](../../mfc/reference/cbasepane-class.md)

