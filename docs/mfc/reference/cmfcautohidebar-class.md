---
title: CMFCAutoHidebar 类
ms.date: 10/18/2018
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
ms.openlocfilehash: 05f77dfba442f1ce4a375c8f225908799ece1788
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751772"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHidebar 类

`CMFCAutoHideBar` 类是实现自动隐藏功能的特殊工具栏类。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|（覆盖[CBasePane：：CalcFixed 布局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).）|
|[CMFCAutoHideBar::Create](#create)|创建控制栏并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。 （覆盖[CPane：创建](../../mfc/reference/cpane-class.md#create).）|
|[CMFCAutoHidebar：获取第一AH窗口](#getfirstahwindow)||
|[CMFCAutoHidebar：获取可见计数](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|当即将显示特殊窗格菜单时由框架调用。 （覆盖[CPane：在显示控制栏菜单](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).）|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|（覆盖[CPane：设置活动组](../../mfc/reference/cpane-class.md#setactiveingroup)。）|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|垂直或水平拉伸窗格。 （覆盖[CBasePane：拉伸窗格](../../mfc/reference/cbasepane-class.md#stretchpane).）|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|用户将鼠标光标放在[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)上的时间延迟与框架显示关联窗口的瞬间之间的时间延迟。|

## <a name="remarks"></a>备注

当用户将停靠窗格切换为自动隐藏模式时，框架会自动创建 `CMFCAutoHideBar` 对象。 它还创建必要的[CAutoHideDockSiteSite](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)对象。 每个 `CAutoHideDockSite` 对象都与单个 `CMFCAutoHideButton` 关联。

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

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFC自动隐藏栏：：添加自动隐藏窗口

向 `CDockablePane` 窗口添加让它能够自动隐藏的功能。

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>参数

*pAutoHidewnd*<br/>
[在]要隐藏的窗口。

*dwalignment*<br/>
[在]指定自动隐藏按钮与应用程序窗口对齐的值。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

*dwAlignment*参数指示自动隐藏按钮驻留在应用程序中的位置。 该参数可为下列任一值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFC自动隐藏栏：：允许显示帕内菜单

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHidebar：：CalcFixed布局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[在]*b 拉伸*<br/>

[在]*布霍兹*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFC自动隐藏栏：CMFC自动隐藏栏

构造 CMFCAutoHideBar 对象。

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHidebar：创建

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

*lpszClass名称*<br/>

*dwStyle*<br/>

*矩形*<br/>

*pparentwnd*<br/>

*nID*<br/>

*dwControlBar样式*<br/>

*pContext*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHidebar：获取第一AH窗口

返回指向应用程序中的第一个自动隐藏窗口的指针。

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>返回值

应用程序中第一个自动隐藏窗口，如果不存在则为 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHidebar：获取可见计数

获取可见自动隐藏按钮的数目。

```
int GetVisibleCount();
```

### <a name="return-value"></a>返回值

返回可见自动隐藏按钮的数目。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHidebar：m_nShowAHWndDelay

用户将鼠标光标放在[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)上的时间延迟与框架显示关联窗口的瞬间之间的时间延迟。

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>备注

当用户将鼠标光标放在 上 时`CMFCAutoHideButton`，框架显示关联的窗口之前会有轻微的延迟。 此参数确定该延迟的长度（以毫秒为单位）。

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFC自动隐藏栏：在显示控制栏菜单

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>参数

[在]*CPoint*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFC自动隐藏栏：删除自动隐藏窗口

删除并销毁自动隐藏窗口。

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>参数

CdockPane® *pAutohided*自动隐藏窗口要删除。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutohidebar：：设置活动组

将自动隐藏栏标记为活动。

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>参数

[在]BOOL *bActive* TRUE 设置为活动状态;否则 FALSE。

### <a name="remarks"></a>备注

请参阅 [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)。

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHidebar：：设置最近可见状态

```cpp
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>参数

bState**<br/>
[在]要设置的状态。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFC自动隐藏栏：显示自动隐藏窗口

显示自动隐藏窗口。

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>参数

*pAutoHidewnd*<br/>
[在]要显示的窗口。

*b显示*<br/>
[在]TRUE 以显示窗口。

*bDelay*<br/>
[在]忽略此参数。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFC自动隐藏栏：拉伸窗格

调整自动隐藏栏在其折叠状态下的大小，以适应 `CMFCAutoHideButton` 对象。

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>参数

*n 长度*<br/>
[在]该值在基本实现中未使用。 在派生的实现中，使用此值可指示已调整大小的窗格的长度。

*bVert*<br/>
[在]该值在基本实现中未使用。 在派生实现中，使用 TRUE 处理自动隐藏栏垂直折叠的情况，对于自动隐藏栏水平折叠的情况，请使用 FALSE。

### <a name="return-value"></a>返回值

已调整大小的窗格的最终大小。

### <a name="remarks"></a>备注

派生的类可以替代此方法以自定义该行为。

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFC自动隐藏栏：：取消设置自动隐藏模式

对一组自动隐藏栏禁用自动隐藏模式。

```cpp
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>参数

[in] pFirstBarInGroup A 指针指向组中的第一个自动隐藏栏。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHidebar：：更新可见状态

由框架在需要重绘自动隐藏栏时调用。

```cpp
void UpdateVisibleState();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFC自动隐藏按钮类](../../mfc/reference/cmfcautohidebutton-class.md)
