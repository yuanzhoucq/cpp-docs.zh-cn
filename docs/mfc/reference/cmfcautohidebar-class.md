---
title: CMFCAutoHideBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3278824e565f34a61943b466ccc6ffef9c4f0be0
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337007"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar 类
`CMFCAutoHideBar` 类是实现自动隐藏功能的特殊工具栏类。  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>语法  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|  
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(重写[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|  
|[CMFCAutoHideBar::Create](#create)|创建控件条，并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。 (重写[cpane:: Create](../../mfc/reference/cpane-class.md#create)。)|  
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||  
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。 (重写[cpane:: Onshowcontrolbarmenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||  
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(重写[cpane:: Setactiveingroup](../../mfc/reference/cpane-class.md#setactiveingroup)。)|  
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||  
|[CMFCAutoHideBar::StretchPane](#stretchpane)|垂直或水平拉伸窗格。 (重写[cbasepane:: Stretchpane](../../mfc/reference/cbasepane-class.md#stretchpane)。)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||  
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|当用户将鼠标光标放在上方的时刻之间的时间延迟[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)的时刻与框架显示关联的窗口。|  
  
## <a name="remarks"></a>备注  
 当用户将停靠窗格切换为自动隐藏模式时，框架会自动创建 `CMFCAutoHideBar` 对象。 它还将创建所需[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)并[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)对象。 每个 `CAutoHideDockSite` 对象都与单个 `CMFCAutoHideButton` 关联。  
  
 `CMFCAutoHideBar` 类在用户鼠标悬停在 `CMFCAutoHideButton` 上方时实现 `CAutoHideDockSite` 的显示。 当工具栏收到 WM_MOUSEMOVE 消息时，`CMFCAutoHideBar` 会启动计时器。 当计时器完成时，它会向工具栏发送 WM_TIMER 事件通知。 工具栏通过检查鼠标指针是否位于它在计时器启动时所处的相同自动隐藏按钮上，来处理此事件。 如果是，则显示附加的 `CAutoHideDockSite`。  
  
 可以通过设置 `m_nShowAHWndDelay` 来控制计时器延迟的长度。 默认值为 400 毫秒。  
  
## <a name="example"></a>示例  
 下列示例演示如何构造 `CMFCAutoHideBar` 对象并使用其 `GetDockSiteRow` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxautohidebar.h  
  
##  <a name="addautohidewindow"></a>  CMFCAutoHideBar::AddAutoHideWindow  
 向 `CDockablePane` 窗口添加让它能够自动隐藏的功能。  
  
```  
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in]*pAutoHideWnd*  
 你想要隐藏的窗口。  
  
 [in]*dwAlignment*  
 用于指定自动隐藏按钮与应用程序窗口对齐方式的值。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 *DwAlignment*参数指示应用程序中的自动隐藏按钮所在的位置。 该参数可为下列任一值：  
  
- CBRS_ALIGN_LEFT  
  
- CBRS_ALIGN_RIGHT  
  
- CBRS_ALIGN_TOP  
  
- CBRS_ALIGN_BOTTOM  
  
##  <a name="allowshowonpanemenu"></a>  CMFCAutoHideBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="calcfixedlayout"></a>  CMFCAutoHideBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in]*bStretch*  
 [in]*bHorz*  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="cmfcautohidebar"></a>  CMFCAutoHideBar::CMFCAutoHideBar  
 构造 CMFCAutoHideBar 对象。  
  
```  
CMFCAutoHideBar();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="create"></a>  CMFCAutoHideBar::Create  

  
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
 [in]*lpszClassName*  
 [in]*dwStyle*  
 [in]*rect*  
 [in]*pParentWnd*  
 [in]*nID*  
 [in]*dwControlBarStyle*  
 [in]*pContext*  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getfirstahwindow"></a>  CMFCAutoHideBar::GetFirstAHWindow  
 返回指向应用程序中的第一个自动隐藏窗口的指针。  
  
```  
CDockablePane* GetFirstAHWindow();
```  
  
### <a name="return-value"></a>返回值  
 应用程序中第一个自动隐藏窗口，如果不存在则为 NULL。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getvisiblecount"></a>  CMFCAutoHideBar::GetVisibleCount  
 获取可见自动隐藏按钮的数目。  
  
```  
int GetVisibleCount();
```  
  
### <a name="return-value"></a>返回值  
 返回可见自动隐藏按钮的数目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_nshowahwnddelay"></a>  CMFCAutoHideBar::m_nShowAHWndDelay  
 当用户将鼠标光标放在上方的时刻之间的时间延迟[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)的时刻与框架显示关联的窗口。  
  
```  
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;  
```  
  
### <a name="remarks"></a>备注  
 当用户将鼠标光标放在上方`CMFCAutoHideButton`，框架显示关联的窗口之前会有轻微延迟。 此参数确定该延迟以毫秒为单位的长度。  
  
##  <a name="onshowcontrolbarmenu"></a>  CMFCAutoHideBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>参数  
 [in]*CPoint*  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="removeautohidewindow"></a>  CMFCAutoHideBar::RemoveAutoHideWindow  
 删除并销毁自动隐藏窗口。  
  
```  
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```  
  
### <a name="parameters"></a>参数  
 CDockablePane * *pAutoHideWnd*  
 要删除的自动隐藏窗口。  
  
### <a name="return-value"></a>返回值  
 若成功，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveingroup"></a>  CMFCAutoHideBar::SetActiveInGroup  
 将自动隐藏栏标记为活动。  
  
```  
virtual void SetActiveInGroup(BOOL bActive);  
```  
  
### <a name="parameters"></a>参数  
 [in]BOOL *bActive*  
 若要设置为活动则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 请参阅[cpane:: Setactiveingroup](../../mfc/reference/cpane-class.md#setactiveingroup)。  
  
##  <a name="setrecentvisiblestate"></a>  CMFCAutoHideBar::SetRecentVisibleState  

  
```  
void SetRecentVisibleState(BOOL bState);
```  
  
### <a name="parameters"></a>参数  
 [in]*bState*  
  
### <a name="remarks"></a>备注  
  
##  <a name="showautohidewindow"></a>  CMFCAutoHideBar::ShowAutoHideWindow  
 显示自动隐藏窗口。  
  
```  
BOOL ShowAutoHideWindow(
        CDockablePane* pAutoHideWnd,  
        BOOL bShow,  
        BOOL bDelay);  
```  
  
### <a name="parameters"></a>参数  
 [in]CDockablePane * *pAutoHideWnd*  
 [in]BOOL *bShow*  
 若要显示窗口，则为 TRUE。  
  
 [in]BOOL *bDelay*  
 忽略此参数。  
  
### <a name="return-value"></a>返回值  
 若成功，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="stretchpane"></a>  CMFCAutoHideBar::StretchPane  
 调整自动隐藏栏在其折叠状态下的大小，以适应 `CMFCAutoHideButton` 对象。  
  
```  
virtual CSize StretchPane(
    int nLength,   
    BOOL bVert);
```  
  
### <a name="parameters"></a>参数  
 [in]*nLength*  
 在基实现中未使用该值。 在派生的实现中，使用此值可指示已调整大小的窗格的长度。  
  
 [in]*bVert*  
 在基实现中未使用该值。 在派生实现中，使用 true 可自动隐藏栏垂直，折叠其中这种情况的句柄和 FALSE 的情况下，自动隐藏栏水平折叠的。  
  
### <a name="return-value"></a>返回值  
 已调整大小的窗格的最终大小。  
  
### <a name="remarks"></a>备注  
 派生的类可以替代此方法以自定义该行为。  
  
##  <a name="unsetautohidemode"></a>  CMFCAutoHideBar::UnSetAutoHideMode  
 对一组自动隐藏栏禁用自动隐藏模式。  
  
```  
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)  
```  
  
### <a name="parameters"></a>参数  
 [in] pFirstBarInGroup  
 指向组中第一个自动隐藏栏的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="updatevisiblestate"></a>  CMFCAutoHideBar::UpdateVisibleState  
 由框架在需要重绘自动隐藏栏时调用。  
  
```  
void UpdateVisibleState();
```  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane 类](../../mfc/reference/cpane-class.md)   
 [CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)
