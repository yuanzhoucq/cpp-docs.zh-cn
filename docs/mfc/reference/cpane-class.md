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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 30edd65a50d3aa20850eace07407a709bd2b837e
ms.lasthandoff: 04/01/2017

---
# <a name="cpane-class"></a>CPane Class
`CPane`类是一项增强功能的[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)。 如果要升级现有 MFC 项目，将出现的所有`CControlBar`与`CPane`。  
  
## <a name="syntax"></a>语法  
  
```  
class CPane : public CBasePane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CPane::~CPane`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新计算一个窗格的布局。|  
|[CPane::AllocElements](#allocelements)|分配存储供内部使用。|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|指定是否将窗格中列出的应用程序的窗格的运行时生成列表中。|  
|[CPane::CalcAvailableSize](#calcavailablesize)|计算大小中指定的矩形和当前窗口矩形之间的差异。|  
|[CPane::CalcInsideRect](#calcinsiderect)|计算内部的窗格中，并考虑边框和控制手柄的矩形。|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|计算最近停靠的矩形。|  
|[CPane::CalcSize](#calcsize)|计算窗格的大小。|  
|[CPane::CanBeDocked](#canbedocked)|确定是否可在指定的基窗格停靠窗格。|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|确定是否可将窗格转换选项卡式文档。|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|将可停靠的窗格中转换为选项卡式文档。|  
|[CPane::CopyState](#copystate)|将复制一个窗格的状态。 (重写[CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate)。)|  
|[Cpane:: Create](#create)|创建的控件条，并将其附加到`CPane`对象。|  
|[Cpane:: Createdefaultminiframe](#createdefaultminiframe)|创建浮动窗格的微型框架窗口。|  
|[Cpane:: Createex](#createex)|创建的控件条，并将其附加到`CPane`对象。|  
|`CPane::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CPane::DockByMouse](#dockbymouse)|使用鼠标停靠方法停靠窗格。|  
|[CPane::DockPane](#dockpane)|浮动窗格停靠到基窗格。|  
|[CPane::DockPaneStandard](#dockpanestandard)|通过使用大纲 （标准） 停靠停靠窗格。|  
|[CPane::DockToFrameWindow](#docktoframewindow)|可停靠窗格停靠到的帧。 （重写 `CBasePane::DockToFrameWindow`。）|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|指示是否可以将停靠在同一行的当前窗格停靠的位置的另一个窗格。|  
|[CPane::FloatPane](#floatpane)|浮动窗格。|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|返回的以像素为单位，可以展开窗格。|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|返回的以像素为单位，可以收缩窗格。|  
|[CPane::GetBorders](#getborders)|返回窗格的边框的宽度。|  
|[CPane::GetClientHotSpot](#getclienthotspot)|返回*作用点*窗格。|  
|[CPane::GetDockSiteRow](#getdocksiterow)|返回在其中停靠窗格的停靠行。|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|确定窗格是否在独占行模式中。|  
|[CPane::GetHotSpot](#gethotspot)|返回存储在基础的热点`CMFCDragFrameImpl`对象。|  
|[CPane::GetMinSize](#getminsize)|检索允许窗格的大小的最小。|  
|[CPane::GetPaneName](#getpanename)|检索窗格的标题。|  
|`CPane::GetResizeStep`|在内部使用。|  
|`CPane::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CPane::GetVirtualRect](#getvirtualrect)|检索*虚拟矩形*的窗格。|  
|[CPane::IsChangeState](#ischangestate)|移动窗格中时，此方法分析相对于其他窗格，停靠行和微型框架窗口的窗格中的位置，并返回相应`AFX_CS_STATUS`值。|  
|[CPane::IsDragMode](#isdragmode)|指定是否要拖动窗格。|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定窗格是否在多窗格框架窗口中。 （重写 `CBasePane::IsInFloatingMultiPaneFrameWnd`。）|  
|[CPane::IsLeftOf](#isleftof)|确定的 （或更高版本） 是否左窗格中指定的矩形。|  
|[CPane::IsResizable](#isresizable)|确定是否可以调整窗格的大小。 (重写[cbasepane:: Isresizable](../../mfc/reference/cbasepane-class.md#isresizable)。)|  
|[CPane::IsTabbed](#istabbed)|确定是否已在选项卡式窗口选项卡控件中插入窗格。 (重写[CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed)。)|  
|[CPane::LoadState](#loadstate)|从注册表加载窗格的状态。 (重写[CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate)。)|  
|[CPane::MoveByAlignment](#movebyalignment)|按指定量移动窗格和虚拟的矩形。|  
|[CPane::MovePane](#movepane)|将窗格移动到指定的矩形。|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|当窗格中的父级发生更改时由框架调用。|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|将要更改的父级的窗格中时，由框架调用。|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|当用户选择关闭按钮上窗格的标题，由框架调用。|  
|`CPane::OnProcessDblClk`|在内部使用。|  
|[Cpane:: Onshowcontrolbarmenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。|  
|[Cpane:: Onshowcontrolbarmenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。|  
|`CPane::PrepareToDock`|在内部使用。|  
|[Cpane:: Recalclayout](#recalclayout)|重新计算该窗格的布局信息。 (重写[CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout)。)|  
|[CPane::SaveState](#savestate)|将窗格的状态保存到注册表。 (重写[CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate)。)|  
|[Cpane:: Setactiveingroup](#setactiveingroup)|将其标记为活动状态的窗格。|  
|[CPane::SetBorders](#setborders)|设置窗格中的边框值。|  
|[CPane::SetClientHotSpot](#setclienthotspot)|设置作用点的窗格。|  
|[CPane::SetDockState](#setdockstate)|还原停靠的窗格的状态信息。|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|启用或禁用独占行模式。|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|设置默认微型框架窗口的运行时类信息。|  
|[CPane::SetMinSize](#setminsize)|设置允许的窗格的大小的最小。|  
|[CPane::SetVirtualRect](#setvirtualrect)|集*虚拟矩形*的窗格。|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|拉伸垂直或水平停靠样式基于的窗格。|  
|[CPane::ToggleAutoHide](#toggleautohide)|切换自动隐藏模式。|  
|[CPane::UndockPane](#undockpane)|从停靠站点、 默认滑块或它当前停靠的微型框架窗口删除窗格。 (重写[CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane)。)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|更新虚拟矩形。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|已停靠窗格时，由框架调用。|  
|[CPane::OnAfterFloat](#onafterfloat)|当已浮动窗格中时，由框架调用。|  
|[CPane::OnBeforeDock](#onbeforedock)|将要停靠窗格时，由框架调用。|  
|[CPane::OnBeforeFloat](#onbeforefloat)|将要浮动窗格中时，由框架调用。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|启用最小大小的窗格的一致处理。|  
|[Cpane:: M_recentdockinfo](#m_recentdockinfo)|包含新停靠的信息。|  
  
## <a name="remarks"></a>备注  
 通常情况下，`CPane`未直接实例化对象。 如果你需要一个具有停靠功能窗格，派生对象从[CDockablePane](../../mfc/reference/cdockablepane-class.md)。 如果需要工具栏功能，派生对象从[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)。  
  
 当你从派生类`CPane`，它可以在中的停靠[CDockSite](../../mfc/reference/cdocksite-class.md)和它可以浮动在[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。  
  
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
 `TRUE`自动重新计算窗格; 的布局否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 动态更改窗格的布局时，请调用此方法。 例如，你可能想要隐藏或显示工具栏按钮时调用此方法。  
  
##  <a name="allocelements"></a>CPane::AllocElements  
 分配存储供内部使用。  
  
```  
BOOL AllocElements(
    int nElements,  
    int cbElement);
```  
  
### <a name="parameters"></a>参数  
 [in] `nElements`  
 为其分配存储空间的元素数目。  
  
 [in] `cbElement`  
 以字节为单位，元素的大小。  
  
### <a name="return-value"></a>返回值  
 `FALSE`如果内存分配失败;否则为`TRUE`。  
  
##  <a name="allowshowonpanemenu"></a>CPane::AllowShowOnPaneMenu  
 指定是否将窗格中列出的应用程序的窗格的运行时生成列表中。  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在列表中; 显示窗格否则为`FALSE`。 基实现始终返回`TRUE`。  
  
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
 包含的大小和偏移量的窗格中的工作区。  
  
 [in] `bHorz`  
 `TRUE`如果在窗格中，面向水平空间。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 它在必须重新计算窗格布局时，将由框架调用此方法。 `rect`参数填充的大小和偏移量的窗格中的工作区。 这包括其边框和控制手柄。  
  
##  <a name="calcrecentdockedrect"></a>CPane::CalcRecentDockedRect  
 计算最近停靠的矩形。  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>备注  
 此方法更新[cpane:: M_recentdockinfo](#m_recentdockinfo)。  
  
##  <a name="calcsize"></a>CPane::CalcSize  
 计算窗格的大小。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>参数  
 [in] `bVertDock`  
 `TRUE`如果垂直停靠窗格`FALSE`否则为。  
  
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
 指定此窗格其中是要停靠的窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此窗格可以停靠在指定的停靠窗格;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法通常称为框架，以确定是否可将一个窗格停靠在指定的停靠窗格。 若要确定是否可以停靠窗格中，该方法的计算结果窗格中的当前启用停靠的对齐方式。  
  
 启用通过调用停靠在框架窗口的各种侧[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="canbetabbeddocument"></a>CPane::CanBeTabbedDocument  
 确定是否可以将窗格转换到选项卡式文档。  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格可以转换到选项卡式文档中。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类中的，并返回`FALSE`如果你想要防止一个窗格转换为选项卡式文档。 未将窗口位置菜单中列出的选项卡式的文档。  
  
##  <a name="converttotabbeddocument"></a>CPane::ConvertToTabbedDocument  
 将可停靠的窗格中转换为选项卡式文档。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActiveTabOnly`  
 中使用不`CPane::ConvertToTabbedDocument`。  
  
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
  
##  <a name="create"></a>Cpane:: Create  
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
 指定的窗格中的 ID。  
  
 [in] `dwControlBarStyle`  
 指定窗格中的样式。 有关详细信息，请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。  
  
 [in][out]`pContext`  
 指定窗格中的创建的上下文。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则已创建了窗格否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法创建一个 Windows 窗格并将其附加到`CPane`对象。  
  
 如果显式未初始化[cpane:: M_recentdockinfo](#m_recentdockinfo)之前调用`Create`，参数`rect`将用作浮动或停靠的窗格中时的矩形。  
  
##  <a name="createdefaultminiframe"></a>Cpane:: Createdefaultminiframe  
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
 由框架创建微型框架窗口时浮动窗格中调用此方法。 微型框架窗口可以是类型[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)或类型的[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)。 如果窗格具有创建多微型框架窗口`AFX_CBRS_FLOAT_MULTI`样式。  
  
 微型框架窗口的运行时类信息存储在`CPane::m_pMiniFrameRTC`成员。 派生的类可用于设置此成员，如果你决定创建自定义的最小化框架窗口。  
  
##  <a name="createex"></a>Cpane:: Createex  
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
 指定窗口样式特性。 有关详细信息，请参阅[窗口样式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和位置`pParentWnd`窗口中的，在工作区坐标。  
  
 [in][out]`pParentWnd`  
 指定此窗格中的父窗口。  
  
 [in] `nID`  
 指定的窗格中的 ID。  
  
 [in] `dwControlBarStyle`  
 指定窗格中的样式。 有关详细信息，请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。  
  
 [in][out]`pContext`  
 指定窗格中的创建上下文。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则已创建了窗格否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法创建一个 Windows 窗格并将其附加到`CPane`对象。  
  
 如果显式未初始化[cpane:: M_recentdockinfo](#m_recentdockinfo)之前调用`CreateEx`，参数`rect`将用作浮动或停靠的窗格中时的矩形。  
  
##  <a name="dockbymouse"></a>CPane::DockByMouse  
 使用鼠标停靠窗格。  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 指定要将此窗格停靠到基本窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠窗格，否则为`FALSE`。  
  
##  <a name="dockpane"></a>CPane::DockPane  
 浮动窗格停靠到基窗格。  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pDockBar`  
 指定的基窗格停靠到此窗格。  
  
 [in] `lpRect`  
 此窗格的停靠位置的基窗格中指定的矩形。  
  
 [in] `dockMethod`  
 指定要使用的停靠方法。 可用选项如下所示︰  
  
|选项|描述|  
|------------|-----------------|  
|`DM_UNKNOWN`|未知停靠方法时，框架将使用此选项。 窗格中不存储其最新的浮动位置。 此选项还可用于以编程方式将窗格停靠时则不需要存储的最新的浮点位置。|  
|`DM_MOUSE`|在内部使用。|  
|`DM_DBL_CLICK`|双击控制手柄时使用此选项。 在其最近的停靠位置重新定位窗格。 如果通过双击连接是窗格中，窗格是在其最新的浮动位置重新定位。|  
|`DM_SHOW`|此选项可以用于以编程方式停靠窗格。 窗格中存储其最新的浮动位置。|  
|`DM_RECT`|窗格停靠在由指定的区域中`lpRect`。|  
|`DM_STANDARD`|当使用此选项时，框架将在窗格中时将被移绘制为大纲帧。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠窗格，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法将窗格停靠到由指定的基窗格`pDockBar`参数。 你必须首先启用通过调用停靠[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="dockpanestandard"></a>CPane::DockPaneStandard  
 通过使用大纲 （标准） 停靠停靠窗格。  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>参数  
 [in] `bWasDocked`  
 `TRUE`如果成功停靠窗格;，否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 此方法始终返回`this`指针。  
  
### <a name="remarks"></a>备注  
 此方法仅用于派生自的窗格[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。 有关详细信息，请参阅[CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard)。  
  
##  <a name="docktoframewindow"></a>CPane::DockToFrameWindow  
 可停靠窗格停靠到的帧。  
  
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
 你想要停靠的窗格中的父框架的一端。  
  
 [in] `lpRect`  
 指定的大小。  
  
 [in] `dwDockFlags`  
 已忽略。  
  
 [in] `pRelativeBar`  
 已忽略。  
  
 [in] `nRelativeIndex`  
 已忽略。  
  
 [in] `bOuterEdge`  
 如果`TRUE`并且没有在指定的一侧其他可停靠窗格`dwAlignment`，窗格停靠在其他窗格中，更接近于父框架边缘。 如果`FALSE`，窗格停靠在更接近的工作区的中心。  
  
### <a name="return-value"></a>返回值  
 `FALSE`如果窗格分隔线 ( [CPaneDivider 类](../../mfc/reference/cpanedivider-class.md)) 创建; 否则为不能为`TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="doesallowsiblingbars"></a>CPane::DoesAllowSiblingBars  
 指示是否可以将停靠在同一行的当前窗格停靠的位置的另一个窗格。  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此窗格可以停靠到另一个窗格与本身; 位于同一行上否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 你可以启用或禁用此行为，通过调用[CPane::SetExclusiveRowMode](#setexclusiverowmode)。  
  
 默认情况下，工具栏具有独占行模式被禁用并且菜单栏启用独占行模式。  
  
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
 在屏幕坐标中，当它浮动定位窗格中指定的位置中。  
  
 [in] `dockMethod`  
 指定要使用时浮动窗格的停靠方法。 有关可能的值的列表，请参阅[CPane::DockPane](#dockpane)。  
  
 [in] `bShow`  
 `TRUE`若要显示窗格时浮动;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功浮动窗格中，或无法浮动窗格中，因为[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)返回`FALSE`; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以浮动在由指定的位置的窗格中`rectFloat`参数。 此方法会自动创建父微型框架窗口的窗格。  
  
##  <a name="getavailableexpandsize"></a>CPane::GetAvailableExpandSize  
 返回的以像素为单位，可以展开窗格。  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果水平停靠的窗格中，则返回值是可用的宽度;否则，返回值是可用的高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getavailablestretchsize"></a>CPane::GetAvailableStretchSize  
 返回的以像素为单位，可以收缩窗格。  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位，窗格可以收缩量。 水平停靠的窗格中，如果此数量是可用的宽度;否则，它是可用的高度。  
  
### <a name="remarks"></a>备注  
 可用的延伸大小通过减去允许的窗格的大小的最小 ( [CPane::GetMinSize](#getminsize)) 从当前大小 ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect))。  
  
##  <a name="getborders"></a>CPane::GetBorders  
 返回窗格的边框的宽度。  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)包含的当前宽度，以像素为单位，每个边窗格中的对象。 例如，值为`left`的成员`CRect`对象是左边框的宽度。  
  
### <a name="remarks"></a>备注  
 若要设置边框的大小，调用[CPane::SetBorders](#setborders)。  
  
##  <a name="getclienthotspot"></a>CPane::GetClientHotSpot  
 返回*作用点*窗格。  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 *作用点*是在用户选择并按住若要将窗格移动的窗格上的点。 作用点用于平滑动画窗格从停靠位置移动时。  
  
##  <a name="getdocksiterow"></a>CPane::GetDockSiteRow  
 返回停靠行 ( [CDockingPanesRow 类](../../mfc/reference/cdockingpanesrow-class.md)) 中窗格停靠。  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>返回值  
 A `CDockingPanesRow`* 指向在其中停靠窗格，停靠行或`NULL`如果未停靠的窗格。  
  
##  <a name="getexclusiverowmode"></a>CPane::GetExclusiveRowMode  
 确定窗格是否在独占行模式中。  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格处于独占行模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 有关独占行模式的详细信息，请参阅[CPane::SetExclusiveRowMode](#setexclusiverowmode)。  
  
##  <a name="gethotspot"></a>CPane::GetHotSpot  
 返回存储在基础的热点`CMFCDragFrameImpl`对象。  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 `CPane`类包含`CMFCDragFrameImpl`对象， `m_dragFrameImpl`，即负责绘制显示当用户在标准停靠模式下将一个窗格的矩形。 作用点用于在用户移动窗格中，绘制矩形相对于当前的鼠标位置。  
  
##  <a name="getminsize"></a>CPane::GetMinSize  
 检索允许窗格的大小的最小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `size`  
 A`CSize`填入允许大小的最小的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpanename"></a>CPane::GetPaneName  
 检索窗格的标题。  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `strName`  
 A`CString`填入的标题名称的对象。  
  
### <a name="remarks"></a>备注  
 停靠或浮动窗格时，会将该窗格标题显示在标题区域中。 如果窗格是选项卡式组的一部分，标题将显示在选项卡区域中。 如果窗格在自动隐藏模式下，标题会显示在`CMFCAutoHideButton`。  
  
##  <a name="getvirtualrect"></a>CPane::GetVirtualRect  
 检索*虚拟矩形*的窗格。  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectVirtual`  
 A`CRect`填入虚拟矩形的对象。  
  
### <a name="remarks"></a>备注  
 窗格中移动时，框架会将窗格中的原始位置存储在一个虚拟的矩形。 该框架可以使用虚拟矩形来还原窗格中的原始位置。  
  
 请勿调用将与虚拟矩形，除非你要以编程方式移动窗格的方法。  
  
##  <a name="ischangestate"></a>CPane::IsChangeState  
 移动窗格中时，此方法将分析其位置相对于其他窗格，停靠行和微型框架窗口，并返回相应`AFX_CS_STATUS`值。  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nOffset`  
 指定停靠的敏感度。 例如，在内移动的窗格`nOffset`将停靠停靠行中的像素为单位。  
  
 [in] `ppTargetBar`  
 方法返回时，`ppTargetBar`包含到应停靠当前窗格中，该对象的指针或`NULL`如果不停靠应发生。  
  
### <a name="return-value"></a>返回值  
 以下项之一`AFX_CS_STATUS`值︰  
  
|值|描述|  
|-----------|-----------------|  
|`CS_NOTHING`|窗格并不是在停靠站点附近。 框架将窗格未停靠。|  
|`CS_DOCK_IMMEDIATELY`|在窗格中，通过停靠站点，与`DT_IMMEDIATE`启用样式。 框架立即停靠窗格。|  
|`CS_DELAY_DOCK`|在窗格中，通过另一个停靠窗格或的主框架边缘停靠站点。 当用户释放移动时，框架将停靠窗格。|  
|`CS_DELAY_DOCK_TO_TAB`|在窗格中，通过使窗格停靠在选项卡式窗口停靠站点。 当窗格时通过另一个停靠窗格的标题或通过选项卡区域的选项卡式窗格中，将发生这种情况。 当用户释放移动时，框架将停靠窗格。|  
  
##  <a name="isdragmode"></a>CPane::IsDragMode  
 指定是否将被移窗格。  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中将被移;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CPane::IsInFloatingMultiPaneFrameWnd  
 指定窗格是否在多窗格框架窗口 ( [CMultiPaneFrameWnd 类](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在窗格中，在多窗格框架窗口;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 仅可停靠窗格可以浮动在多窗格中框架窗口中。 因此，`CPane::IsInFloatingMultiPaneFrameWnd`始终返回`FALSE`。  
  
##  <a name="isleftof"></a>CPane::IsLeftOf  
 确定的 （或更高版本） 是否左窗格中指定的矩形。  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 A`CRect`用于比较的对象。  
  
 [in] `bWindowRect`  
 如果`TRUE`，`rect`假定包含屏幕坐标; 如果`FALSE`，`rect`假定包含客户端坐标。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 如果水平停靠的窗格中，此方法检查是否将其位置左下的`rect`。 否则，此方法检查位置是否高于`rect`。  
  
##  <a name="isresizable"></a>CPane::IsResizable  
 指定是否可调整大小的窗格。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在窗格中，可调整大小;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 基本`CPane`对象不是可调整大小。  
  
 到停靠管理器使用可调整大小的标志来确定窗格布局。 非可调整大小的窗格始终是位于父框架的外边缘的。  
  
 非可调整大小的窗格不能驻留在停靠容器。  
  
##  <a name="istabbed"></a>CPane::IsTabbed  
 确定窗格中是否已插入到选项卡控件的选项卡式窗口。  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格选项卡式;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 选项卡式的状态都将单独处理从浮点、 停靠，和自动隐藏状态。  
  
##  <a name="loadstate"></a>CPane::LoadState  
 从注册表加载窗格的状态。  
  
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
 窗格中的 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则加载窗格状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以从注册表加载窗格状态。 在由保存要加载的其他信息的派生类中重写它[CPane::SaveState](#savestate)。  
  
 当你重写此方法时，还调用基方法，并返回`FALSE`如果基方法返回`FALSE`。  
  
##  <a name="m_bhandleminsize"></a>CPane::m_bHandleMinSize  
 启用一致处理的最小窗格大小。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>备注  
 如果在你的应用程序中的一个或多个停靠窗格重写`GetMinSize`，或如果你的应用程序调用`SetMinSize`，你可能想要将此静态成员设置为`TRUE`要使框架，一致地处理窗格将调整的大小。  
  
 如果此值设置为`TRUE`，其大小应减小其最小大小下的所有窗格将被都剪辑，未延伸。 由于框架将用于窗格大小调整用途的窗口区域，请不要更改此值设置为如果停靠窗格的窗口区域的大小`TRUE`。  
  
##  <a name="m_recentdockinfo"></a>Cpane:: M_recentdockinfo  
 包含新停靠的信息。  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>备注  
 框架将存储在此成员的窗格中的最新停靠状态信息。  
  
##  <a name="movebyalignment"></a>CPane::MoveByAlignment  
 按指定量移动窗格和虚拟的矩形。  
  
```  
BOOL MoveByAlignment(
    DWORD dwAlignment,  
    int nOffset);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定窗格对齐方式。  
  
 [in] `nOffset`  
 以像素为单位，用于移动窗格和虚拟矩形量。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 `dwAlignment`可以是任何以下值︰  
  
|值|说明|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|启用到框架窗口的工作区顶部停靠的窗格。|  
|`CBRS_ALIGN_BOTTOM`|启用到框架窗口的工作区底部停靠的窗格。|  
|`CBRS_ALIGN_LEFT`|启用要停靠框架窗口的客户端区域的左侧窗格。|  
|`CBRS_ALIGN_RIGHT`|使框架窗口的工作区右侧停靠的窗格。|  
|`CBRS_ALIGN_ANY`|启用到框架窗口的工作区的任何一侧停靠的窗格。|  
  
 如果`dwAlignment`包含`CBRS_ALIGN_LEFT`或`CBRS_ALIGN_RIGHT`标志、 窗格和虚拟矩形被移动水平; 否则为如果`dwAlignment`包含`CBRS_ALIGN_TOP`或`CBRS_ALIGN_BOTTOM`标志、 窗格和虚拟矩形被垂直移动。  
  
##  <a name="movepane"></a>CPane::MovePane  
 将窗格移动到指定的矩形。  
  
```  
virtual CSize MovePane(
    CRect rectNew,  
    BOOL bForceMove,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectNew`  
 指定新添加的矩形的窗格。  
  
 [in] `bForceMove`  
 如果`TRUE`，此方法将忽略的最小允许的窗格大小 ( [CPane::GetMinSize](#getminsize)); 否则为调整窗格中，如有必要，以确保它至少是允许大小的最小。  
  
 [in] `hdwp`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 A`CSize`对象，其中包含之间的新和旧的矩形的宽度和高度差异 (旧矩形- `rectNew`)。  
  
### <a name="remarks"></a>备注  
 此方法仅用于可停靠窗格。  
  
##  <a name="onafterchangeparent"></a>CPane::OnAfterChangeParent  
 当窗格中的父级发生更改时由框架调用。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pWndOldParent`  
 窗格的上一个父窗口。  
  
### <a name="remarks"></a>备注  
 由于停靠或浮动操作更改后的父级的窗格中，将由框架调用此方法。  
  
##  <a name="onafterdock"></a>CPane::OnAfterDock  
 已停靠窗格时，由框架调用。  
  
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
 后一个窗格浮动，由框架调用。  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>备注  
 如果你想要执行任何处理后浮动窗格中，可以重写此方法在派生类中。  
  
##  <a name="onbeforechangeparent"></a>CPane::OnBeforeChangeParent  
 将要更改的父级的窗格中时，由框架调用。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pWndNewParent`  
 指定新的父窗口。  
  
 [in] `bDelay`  
 `TRUE`对延迟全局的停靠布局调整;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 将要更改，因为正在窗格中的父级的窗格中时，由框架调用此方法停靠或浮动。  
  
 默认情况下，在窗格中，与停靠窗格注销通过调用`CDockSite::RemovePane`。  
  
##  <a name="onbeforedock"></a>CPane::OnBeforeDock  
 将要停靠窗格时，由框架调用。  
  
```  
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`ppDockBar`  
 指定此窗格停靠到窗格。  
  
 [in] `lpRect`  
 指定的停靠的矩形。  
  
 [in] `dockMethod`  
 指定的停靠的方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以停靠窗格。 如果该函数将返回`FALSE`，停靠操作将中止。  
  
### <a name="remarks"></a>备注  
 将要停靠窗格时，将由框架调用此方法。 如果你想要执行任何处理之前最后停靠窗格中，可以重写此方法在派生类中。  
  
##  <a name="onbeforefloat"></a>CPane::OnBeforeFloat  
 当窗格时有关为浮点数，由框架调用。  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectFloat`  
 当它处于浮动状态时指定的位置和窗格的大小。  
  
 [in] `dockMethod`  
 指定的停靠窗格的方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以浮动窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当窗格时有关为浮点数，由框架调用此方法。 如果你想要执行任何处理之前最后浮动窗格中，可以重写此方法在派生类中。  
  
##  <a name="onpressclosebutton"></a>CPane::OnPressCloseButton  
 当用户按关闭按钮上窗格的标题时，由框架调用。  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>备注  
 当用户按下时，由框架调用此方法**关闭**上窗格的标题按钮。 若要接收通知有关**关闭**事件，你可以重写此方法在派生类中的。  
  
##  <a name="onshowcontrolbarmenu"></a>Cpane:: Onshowcontrolbarmenu  
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
 菜单包含多个项，使您能够指定窗格的行为，即︰**浮动**，**停靠**，**自动隐藏**，和**隐藏**。 你可以通过调用启用所有窗格此菜单[CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu)。  
  
##  <a name="recalclayout"></a>Cpane:: Recalclayout  
 重新计算该窗格的布局信息。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 如果窗格停靠，此方法将更新通过将其大小设置为窗格中的当前大小的窗格中的虚拟矩形。  
  
 如果窗格浮动的此方法将通知父微型框架，以调整微型框架的大小的窗格中的大小。 框架可确保的最小化框架至少是允许的窗格的大小的最小 ( [CPane::GetMinSize](#getminsize)) 并调整其大小微型框架，如有必要。  
  
##  <a name="savestate"></a>CPane::SaveState  
 将窗格的状态保存到注册表。  
  
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
 窗格中的 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则保存状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法时它将窗格的状态保存到注册表。 重写`SaveState`在派生类来存储的其他信息。  
  
 当你重写此方法时，还调用基方法，并返回`FALSE`如果基方法返回`FALSE`。  
  
##  <a name="setactiveingroup"></a>Cpane:: Setactiveingroup  
 将其标记为活动状态的窗格。  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActive`  
 A `BOOL` ，它指定是否已标记的窗格中为活动状态。  
  
### <a name="remarks"></a>备注  
 如果可停靠的窗格中所示，或选择一个自动隐藏按钮，相应的自动隐藏窗格标记为活动状态。  
  
 与窗格中的自动隐藏按钮的外观取决于两个因素。 如果窗格处于活动状态，与`static``BOOL``CMFCAutoHideButton::m_bOverlappingTabs`是`TRUE`，框架将自动隐藏按钮显示为图标和标签。 对于处于非活动状态的窗格中，框架显示自动隐藏图标。  
  
 如果`CMFCAutoHideButton::m_bOverlappingTabs`是`FALSE`，或如果组中未位于窗格中，框架会将关联的自动隐藏按钮显示为图标和标签。  
  
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
 指定以像素为单位，窗格的左边框的宽度。  
  
 [in] `cyTop`  
 指定以像素为单位，窗格的上边框的宽度。  
  
 [in] `cxRight`  
 指定以像素为单位，窗格的右边框的宽度。  
  
 [in] `cyBottom`  
 指定以像素为单位，窗格的下边框的宽度。  
  
 [in] `lpRect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含的宽度，以像素为单位，每个窗格的边框。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置窗格的边框的大小。  
  
##  <a name="setclienthotspot"></a>CPane::SetClientHotSpot  
 集*作用点*窗格。  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `ptNew`  
 A`CPoint`对象，它指定新的作用点。  
  
### <a name="remarks"></a>备注  
 *作用点*是在用户选择并按住若要将窗格移动的窗格上的点。 作用点用于平滑动画时从停靠位置拖动该窗格。  
  
##  <a name="setdockstate"></a>CPane::SetDockState  
 还原停靠的窗格的状态信息。  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockManager`  
 指向主框架窗口到停靠管理器的指针。  
  
### <a name="remarks"></a>备注  
 由框架还原窗格停靠的最近状态信息调用此方法。 窗格中将存储在最近的停靠状态信息[cpane:: M_recentdockinfo](#m_recentdockinfo)。 有关详细信息，请参阅[CRecentDockSiteInfo 类](../../mfc/reference/crecentdocksiteinfo-class.md)。  
  
 你还可以调用此方法以设置停靠状态，当你从外部源加载窗格中的信息。  
  
##  <a name="setexclusiverowmode"></a>CPane::SetExclusiveRowMode  
 启用或禁用独占行模式。  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bExclusive`  
 `TRUE`若要启用独占行模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以启用或禁用独占行模式。 在独占行模式下一个窗格时，它不能与任何其他工具栏共享同一行。  
  
 默认情况下，所有工具栏都具有独占行模式被禁用并且菜单栏启用独占行模式。  
  
##  <a name="setminsize"></a>CPane::SetMinSize  
 设置允许的窗格的大小的最小。  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>参数  
 [in] `size`  
 A`CSize`包含允许的窗格的大小的最小的对象。  
  
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
 A`CRect`对象，它指定要设置的虚拟矩形。  
  
 [in] `bMapToParent`  
 指定`TRUE`如果`rect`包含相对于父窗口的点。  
  
### <a name="remarks"></a>备注  
 A*虚拟矩形*移动时，将存储一个窗格的原始位置。 该框架可以使用虚拟矩形来还原原始位置。  
  
 请勿调用将与虚拟矩形，除非你要以编程方式移动窗格的方法。  
  
##  <a name="setminiframertc"></a>CPane::SetMiniFrameRTC  
 设置默认微型框架窗口的运行时类信息。  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pClass`  
 指定微型框架窗口的运行时类信息。  
  
### <a name="remarks"></a>备注  
 当浮动窗格中时，它将被放[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) （微型框架） 窗口。 你可以提供自定义`CPaneFrameWnd`-派生类将时使用[cpane:: Createdefaultminiframe](#createdefaultminiframe)调用。  
  
##  <a name="stretchpanedeferwndpos"></a>CPane::StretchPaneDeferWndPos  
 拉伸垂直或水平停靠样式基于的窗格。  
  
```  
virtual int StretchPaneDeferWndPos(
    int nStretchSize,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>参数  
 [in] `nStretchSize`  
 量，以像素为单位，要拉伸窗格。 使用负值收缩窗格。  
  
 [in] `hdwp`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 实际的量，以像素为单位，窗格已延伸。  
  
### <a name="remarks"></a>备注  
 如果有必要，此方法会修改`nStretchSize`以确保窗格不超过大小限制。 通过调用获得这些限制[CPane::GetAvailableStretchSize](#getavailablestretchsize)和[CPane::GetAvailableExpandSize](#getavailableexpandsize)。  
  
##  <a name="toggleautohide"></a>CPane::ToggleAutoHide  
 切换自动隐藏模式。  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>备注  
 调用此方法以切换自动隐藏模式。 若要切换到自动隐藏模式，必须到主框架窗口停靠窗格。  
  
##  <a name="undockpane"></a>CPane::UndockPane  
 从停靠站点、 默认滑块或它当前停靠的微型框架窗口删除窗格。  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDelay`  
 如果`FALSE`，框架调用[cbasepane:: Adjustdockinglayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)以调整停靠布局。  
  
### <a name="remarks"></a>备注  
 使用此方法以编程方式取消停靠窗格。  
  
##  <a name="updatevirtualrect"></a>CPane::UpdateVirtualRect  
 更新虚拟矩形。  
  
```  
void UpdateVirtualRect();  
void UpdateVirtualRect(CPoint ptOffset);  
  void UpdateVirtualRect(CSize sizeNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `ptOffset`  
 A`CPoint`对象，它指定移位窗格中的偏移量。  
  
 [in] `sizeNew`  
 A`CSize`对象，它指定窗格中的新大小。  
  
### <a name="remarks"></a>备注  
 第一个重载使用的当前的位置和大小的窗格中的设置虚拟矩形。  
  
 第二个重载右移指定的量虚拟矩形`ptOffset`。  
  
 第三个重载使用当前位置窗格和由指定的大小的设置的虚拟矩形`sizeNew`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CBasePane 类](../../mfc/reference/cbasepane-class.md)

