---
title: CPaneFramewnd 类
ms.date: 11/04/2016
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
ms.openlocfilehash: 76f7c5c2c21f0e823545db3669ce454c8172317c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753609"
---
# <a name="cpaneframewnd-class"></a>CPaneFramewnd 类

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

实现包含一个窗格的微型框架窗口。 此窗格填满窗口的工作区。

## <a name="syntax"></a>语法

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|添加窗格。|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|从全局列表添加或删除窗格。|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|调整微型框架窗口的布局。|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|计算微型框架窗口的边框大小。|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|计算停靠窗口的预期矩形。|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|确定是否可将当前窗格停靠到另一个窗格或框架窗口。|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|确定是否可将微型框架窗口停靠到窗格。|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|将窗格转换为选项卡式文档。|
|[CPaneFrameWnd::Create](#create)|创建微型框架窗口，并将其附加到 `CPaneFrameWnd` 对象。|
|[CPaneFrameWnd::CreateEx](#createex)|创建微型框架窗口，并将其附加到 `CPaneFrameWnd` 对象。|
|[CPaneFrameWnd::DockPane](#dockpane)|停靠窗格。|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|在浮动窗格的全局列表中查找具有指定控件 ID 的窗格。|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|查找包含用户提供的点的微型框架窗口。|
|[CPaneFramewnd：：获取标题高度](#getcaptionheight)|返回微型框架窗口标题的高度。|
|[CPaneFramewnd：：获取字幕](#getcaptionrect)|计算微型框架窗口标题的边框矩形。|
|[CPaneFramewnd：：获取字幕文本](#getcaptiontext)|返回标题文本。|
|[CPaneFramewnd：：获取停靠管理器](#getdockingmanager)||
|[CPaneFramewnd：：获取停靠模式](#getdockingmode)|返回停靠模式。|
|[CPaneFramewnd：：获取第一个可见窗格](#getfirstvisiblepane)|返回包含在微型框架窗口中的第一个可见窗格。|
|[CPaneFramewnd：获取HotPoint](#gethotpoint)||
|[CPaneFramewnd：：获取窗格](#getpane)|返回包含在微型框架窗口中的窗格。|
|[CPaneFramewnd：：获取窗格计数](#getpanecount)|返回包含在微型框架窗口中的窗格数。|
|[CPaneFramewnd：：获取父级](#getparent)||
|[CPaneFramewnd：：GetPinstate](#getpinstate)||
|[CPaneFramewnd：：获取最新浮动](#getrecentfloatingrect)||
|[CPaneFramewnd：：获取可见窗格计数](#getvisiblepanecount)|返回包含在微型框架窗口中的可见窗格数。|
|[CPaneFrameWnd::HitTest](#hittest)|确定微型框架窗口的哪一部分位于给定点。|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|确定是否应下滚微型框架窗口。|
|[CPaneFrameWnd::IsRollUp](#isrollup)|确定是否应上滚微型框架窗口。|
|[CPaneFramewnd：：杀死对接计时器](#killdockingtimer)|停止停靠计时器。|
|[CPaneFrameWnd::LoadState](#loadstate)|从注册表加载窗格的状态。|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|确定停靠是否可能。|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|将微型框架窗口停靠在其最新的位置。|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|停止汇总计时器。|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|按指定偏移量移动微型框架窗口。|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|调整包含的窗格的布局。|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|设置汇总计时器。|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|隐藏或显示微型框架窗口的窗格时，由框架进行调用。|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|类[CWinApp](../../mfc/reference/cwinapp-class.md)在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前，用于转换窗口消息。|
|[CPaneFrameWnd::RedrawAll](#redrawall)|重绘所有微型框架窗口。|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|由框架调用以删除非有效窗格。|
|[CPaneFrameWnd::RemovePane](#removepane)|从微型框架窗口删除窗格。|
|[CPaneFrameWnd::ReplacePane](#replacepane)|用一个窗格替换另一个窗格。|
|[CPaneFrameWnd::SaveState](#savestate)|将窗格的状态保存到注册表。|
|`CPaneFrameWnd::Serialize`|从存档读取该对象或将该对象写入存档。|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|设置标题按钮。|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|设置停靠计时器。|
|[CPaneFrameWnd::SetDockState](#setdockstate)|设置停靠状态。|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|由框架调用以设置预停靠状态。|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|调整微型框架窗口大小，使其大小等于包含窗格的大小。|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|移走菜单。|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|确定是否应上滚或下滚微型框架窗口。|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|绘制微型框架窗口的边框。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|指定是否使用CS_SAVEBITS类样式注册窗口类。|

## <a name="remarks"></a>备注

当窗格从停靠状态切换到浮动状态时，框架会自动创建 `CPaneFrameWnd` 对象。

可使用其可见内容（立即停靠）或拖动矩形（标准停靠）来拖动微型框架窗口。 微型框架的容器窗格的停靠模式确定微型框架的拖动行为。 有关详细信息，请参阅[CbasePane：：获取停靠模式](../../mfc/reference/cbasepane-class.md#getdockingmode)。

微型框架窗口根据包含的窗格样式在标题上显示按钮。 如果窗格可以关闭[（CBasePane：：可以关闭](../../mfc/reference/cbasepane-class.md#canbeclosed)），它将显示一个关闭按钮。 如果窗格具有AFX_CBRS_AUTO_ROLLUP样式，则显示一个引脚。

如果从 `CPaneFrameWnd` 派生类，则必须告诉框架如何创建类。 通过重写[CPane：：createDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)创建类，或者设置`CPane::m_pMiniFrameRTC`成员，以便它指向类的运行时类信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>要求

**标题：** afxPaneFramewnd.h

## <a name="cpaneframewndaddpane"></a><a name="addpane"></a>CPaneFramed：：添加窗格

添加窗格。

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]要添加的窗格。

## <a name="cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a>CPaneFramewnd：：从全局列表添加删除窗格

从全局列表添加或删除窗格。

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]要添加或删除的窗格。

*bAdd*<br/>
[在]如果为非零，则添加窗格。 如果为 0，请删除窗格。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

## <a name="cpaneframewndadjustlayout"></a><a name="adjustlayout"></a>CPaneFramed：：调整布局

调整微型框架窗口的布局。

```
virtual void AdjustLayout();
```

## <a name="cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CPaneFramed：：调整窗格框架

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

## <a name="cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a>CPaneFramewnd：：钙边界大小

计算小型框架窗口的边框大小。

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>参数

*整边界大小*<br/>
[出]包含小型框架窗口边框的大小（以像素为单位）。

### <a name="remarks"></a>备注

框架调用此方法以计算小型框架窗口的边框大小。 返回的大小取决于小型框架窗口是否包含工具栏或[CDockablePane](../../mfc/reference/cdockablepane-class.md)。

## <a name="cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneFramewnd：：卡尔奇德多克德雷ct

计算停靠窗口的预期矩形。

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>参数

*普恩德托多克*<br/>
[在]指向要停靠的窗口的指针。

*ptMouse*<br/>
[在]鼠标位置。

*rectResult*<br/>
[出]计算的矩形。

*bDrawTab*<br/>
[出]如果为 TRUE，则绘制一个选项卡。如果 FALSE，则不要绘制选项卡。

*ppTargetBar*<br/>
[出]指向目标窗格的指针。

### <a name="remarks"></a>备注

此方法计算当用户将窗口拖动到*ptMouse*指定的点并将其停靠在那里时，窗口将占用的矩形。

## <a name="cpaneframewndcanbeattached"></a><a name="canbeattached"></a>CPaneFramewnd：：可以附加

确定是否可将当前窗格停靠到另一个窗格或框架窗口。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

如果窗格可以停靠到另一个窗格或框架窗口，则为 TRUE;否则 FALSE。

## <a name="cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CPaneframewnd：：可以多克托帕

确定是否可将微型框架窗口停靠到窗格。

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>参数

*pDockingBar*<br/>
[在]窗格。

### <a name="return-value"></a>返回值

如果微型框架可以停靠到*pDockingBar，* 则非零。否则 0。

## <a name="cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CPaneFramewnd：：检查夹持者可见性

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>备注

## <a name="cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPaneframewnd：：转换到标签文档

将窗格转换为选项卡式文档。

```
virtual void ConvertToTabbedDocument();
```

## <a name="cpaneframewndcreate"></a><a name="create"></a>CPaneFramewnd：：创建

创建一个小型框架窗口并将其附加到[CPaneFramewnd](../../mfc/reference/cpaneframewnd-class.md)对象。

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*lpsz窗口名称*<br/>
[在]指定要在小型框架窗口中显示的文本。

*dwStyle*<br/>
[在]指定窗口样式。 有关详细信息，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*矩形*<br/>
[在]指定小型框架窗口的初始大小和位置。

*pparentwnd*<br/>
[进出]指定小型框架窗口的父帧。 此值不能为 NULL。

*pContext*<br/>
[进出]指定用户定义的上下文。

### <a name="return-value"></a>返回值

如果成功创建窗口，则为 TRUE;如果窗口已成功创建，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

分两步创建小型框架窗口。 首先，框架创建一个`CPaneFrameWnd`对象。 其次，它调用`Create`创建 Windows 小型框架窗口并将其附加到`CPaneFrameWnd`对象。

## <a name="cpaneframewndcreateex"></a><a name="createex"></a>CPaneFramewnd：：创建Ex

创建一个小型框架窗口并将其附加到[CPaneFramewnd](../../mfc/reference/cpaneframewnd-class.md)对象。

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>参数

*dwStyleEx*<br/>
[在]指定扩展的窗口样式。 有关详细信息，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpsz窗口名称*<br/>
[在]指定要在小型框架窗口中显示的文本。

*dwStyle*<br/>
[在]指定窗口样式。 有关详细信息，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*矩形*<br/>
[在]指定小型框架窗口的初始大小和位置。

*pparentwnd*<br/>
[进出]指定小型框架窗口的父帧。 此值不能为 NULL。

*pContext*<br/>
[进出]指定用户定义的上下文。

### <a name="return-value"></a>返回值

如果成功创建窗口，则为 TRUE;如果窗口已成功创建，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

分两步创建小型框架窗口。 首先，框架创建一个`CPaneFrameWnd`对象。 其次，它调用`Create`创建 Windows 小型框架窗口并将其附加到`CPaneFrameWnd`对象。

## <a name="cpaneframewnddockpane"></a><a name="dockpane"></a>CPaneFramewnd：:DockPane

停靠窗格。

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>参数

*bWasdocked*<br/>
[出]如果窗格已停靠，则为 TRUE;否则 FALSE。

### <a name="return-value"></a>返回值

如果操作成功，`CDockablePane`则窗格停靠到 ;否则 NULL。

## <a name="cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a>CPaneFramewnd：：查找浮动窗格

在浮动窗格的全局列表中查找具有指定控件 ID 的窗格。

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]表示要查找的窗格的控制 ID。

### <a name="return-value"></a>返回值

具有指定控件 ID 的窗格;否则，NULL，如果没有窗格具有指定的控件 ID。

## <a name="cpaneframewndframefrompoint"></a><a name="framefrompoint"></a>CPaneFramewnd：：框架从点

查找包含指定点的微型框架窗口。

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>参数

*pt*<br/>
[在]点，在屏幕坐标。

*nSensitivity*<br/>
[在]按此大小增加微型框架窗口的搜索区域。 如果给定点落在增加的区域中，则微型框架窗口满足搜索条件。

*pFrame 排除*<br/>
[在]指定要从搜索中排除的微型框架窗口。

*b 浮动多只*<br/>
[在]如果为 TRUE，则仅搜索具有CBRS_FLOAT_MULTI样式的微型框架窗口。 如果 FALSE，则搜索所有微型框架窗口。

### <a name="return-value"></a>返回值

指向包含*pt*的微型框架窗口的指针。否则 NULL。

## <a name="cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a>CPaneFramewnd：：获取标题高度

返回微型框架窗口标题的高度。

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>返回值

微型框架窗口的高度（以像素为单位）。

### <a name="remarks"></a>备注

调用此方法以确定微型框架窗口的高度。 默认情况下，高度设置为SM_CYSMCAPTION。 有关详细信息，请参阅[获取系统度量函数](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)。

## <a name="cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a>CPaneFramewnd：：获取字幕

计算微型框架窗口标题的边框矩形。

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>参数

*rectCaption*<br/>
[出]在屏幕坐标中包含迷你框架窗口标题的大小和位置。

### <a name="remarks"></a>备注

框架调用此方法以计算小型框架窗口标题的边界矩形。

## <a name="cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CPaneFramewnd：：获取字幕文本

返回标题文本。

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>返回值

微型框架窗口的标题文本。

### <a name="remarks"></a>备注

当框架显示标题文本时，它调用此方法。

## <a name="cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a>CPaneFramewnd：：获取停靠管理器

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a>CPaneFramewnd：：获取停靠模式

返回停靠模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>返回值

停靠模式。 以下值之一：

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

## <a name="cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CPaneFramewnd：：获取第一个可见窗格

返回包含在微型框架窗口中的第一个可见窗格。

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>返回值

如果微型框架窗口不包含窗格，则微型框架窗口中的第一个窗格为 NULL。

## <a name="cpaneframewndgethotpoint"></a><a name="gethotpoint"></a>CPaneFramewnd：获取HotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetpane"></a><a name="getpane"></a>CPaneFramewnd：：获取窗格

返回包含在微型框架窗口中的窗格。

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>返回值

如果微型框架窗口不包含窗格，则包含在微型框架中的窗格或 NULL。

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetpanecount"></a><a name="getpanecount"></a>CPaneFramewnd：：获取窗格计数

返回包含在微型框架窗口中的窗格数。

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>返回值

迷你框架窗口中的窗格数。 此值可以为零。

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetparent"></a><a name="getparent"></a>CPaneFramewnd：：获取父级

```
CWnd* GetParent();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetpinstate"></a><a name="getpinstate"></a>CPaneFramewnd：：GetPinstate

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a>CPaneFramewnd：：获取最新浮动

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CPaneFramewnd：：获取可见窗格计数

返回包含在微型框架窗口中的可见窗格数。

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>返回值

可见窗格的数量。

### <a name="remarks"></a>备注

## <a name="cpaneframewndhittest"></a><a name="hittest"></a>CPaneFramewnd：：HitTest

确定微型框架窗口的哪一部分位于给定点。

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]要测试的点。

*b 检测标题*<br/>
[在]如果为 TRUE，则对照标题检查该点。 如果 FALSE，请忽略标题。

### <a name="return-value"></a>返回值

以下值之一：

|“值”|含义|
|-----------|-------------|
|HTNOWHERE|点在微型框架窗口外。|
|HTClient|点位于工作区中。|
|HTCAPTION|要点在标题上。|
|HTTOP|点在顶部。|
|HTTOPLEFT|点在左上角。|
|赫托普赖特|点在右上角。|
|HTLEFT|点在左边。|
|HTRIGHT|关键是右边。|
|HTBOTTOM|点在底部。|
|HTBOTTOMLEFT|点在左下角。|
|HTBOTTOMRIGHT|点在右下角。|

## <a name="cpaneframewndiscaptured"></a><a name="iscaptured"></a>CPaneFramewnd：：已捕获

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndisdelayshow"></a><a name="isdelayshow"></a>CPaneFramewnd：：延迟显示

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cpaneframewndisrolldown"></a><a name="isrolldown"></a>CPaneFramewnd：：滚落

确定是否应下滚微型框架窗口。

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>返回值

如果必须向下滚动微型框架窗口，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

框架调用此方法以确定是否应向下滚动小型框架窗口。 如果微型框架窗口至少包含一个具有AFX_CBRS_AUTO_ROLLUP标志的窗格，则为该窗口启用汇总/滚动功能。 创建窗格时设置此标志。 有关详细信息，请参阅[CBasePane：：创建Ex](../../mfc/reference/cbasepane-class.md#createex)。

默认情况下，框架检查鼠标指针是否位于小型框架窗口边界矩形内，以确定是否必须向下滚动窗口。 可以在派生类中重写此行为。

## <a name="cpaneframewndisrollup"></a><a name="isrollup"></a>CPaneFramewnd：：Isrollup

确定是否应上滚微型框架窗口。

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>返回值

如果必须卷起微型框架窗口，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

框架调用此方法以确定是否应汇总小型框架窗口。 如果微型框架窗口至少包含一个具有AFX_CBRS_AUTO_ROLLUP标志的窗格，则为该窗口启用汇总/滚动功能。 创建窗格时设置此标志。 有关详细信息，请参阅[CBasePane：：创建Ex](../../mfc/reference/cbasepane-class.md#createex)。

默认情况下，框架检查鼠标指针是否位于小型框架窗口边界矩形内，以确定是否必须汇总窗口。 可以在派生类中重写此行为。

## <a name="cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a>CPaneFramewnd：：杀死对接计时器

停止停靠计时器。

```cpp
void KillDockingTimer();
```

## <a name="cpaneframewndloadstate"></a><a name="loadstate"></a>CPaneFramewnd：：加载状态

从注册表加载窗格的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]配置文件名称。

*uiID*<br/>
[在]窗格 ID。

### <a name="return-value"></a>返回值

如果窗格状态已成功加载，则为 TRUE;如果窗格状态已成功加载，则为 TRUE。否则 FALSE。

## <a name="cpaneframewndm_busesavebits"></a><a name="m_busesavebits"></a>CPaneFramewnd：：m_bUseSaveBits

指定是否注册具有类样式CS_SAVEBITS的窗口类。

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>备注

将此静态成员设置为 TRUE 以注册具有CS_SAVEBITS样式的微型框架窗口类。 当用户拖动微型框架窗口时，这可能有助于减少闪烁。

## <a name="cpaneframewndonbeforedock"></a><a name="onbeforedock"></a>CPaneFramewnd：：在Dock前

确定停靠是否可能。

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>返回值

如果可以停靠，则为 TRUE;否则，FALSE。

## <a name="cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a>CPaneFramewnd：：在Checkrollstate

确定是否应上滚或下滚微型框架窗口。

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>备注

框架调用此方法以确定是否应向上或向下滚动小型框架窗口。

默认情况下，框架称为[CPaneFramewnd：：IsRollUp](#isrollup)和[CPaneFramewnd：：IsRollDown，](#isrolldown)只是拉伸或还原微型框架窗口。 可以在派生类中重写此方法以使用不同的视觉效果。

## <a name="cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CPaneframewnd：：在多克到最近的Pos

将微型框架窗口停靠在其最新的位置。

```
virtual void OnDockToRecentPos();
```

## <a name="cpaneframewndondrawborder"></a><a name="ondrawborder"></a>CPaneFramewnd：：在绘制边框

绘制微型框架窗口的边框。

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]用于绘制边框的设备上下文。

### <a name="remarks"></a>备注

框架调用此方法以绘制小型框架窗口的边框。

## <a name="cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CPaneFramewnd：：在基基尔罗普普计时器上

停止汇总计时器。

```
virtual void OnKillRollUpTimer();
```

## <a name="cpaneframewndonmovepane"></a><a name="onmovepane"></a>CPaneFramewnd：：移动窗格

按指定偏移量移动微型框架窗口。

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]指向窗格的指针（忽略）。

*pt偏移*<br/>
[在]要移动窗格的偏移量。

## <a name="cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CPaneFramewnd：：在PaneRecalc布局上

调整小型框架窗口中窗格的布局。

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>备注

当框架必须在微型框架窗口中调整窗格的布局时，它将调用此方法。

默认情况下，窗格定位为覆盖微型框架窗口的完整工作区。

## <a name="cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CPaneFramewnd：：上接龙器定时器

设置汇总计时器。

```
virtual void OnSetRollUpTimer();
```

## <a name="cpaneframewndonshowpane"></a><a name="onshowpane"></a>CPaneFramewnd：：在显示窗格上

隐藏或显示微型框架窗口的窗格时，由框架进行调用。

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[在]正在显示或隐藏的窗格。

*b显示*<br/>
[在]如果显示窗格，则为 TRUE;如果窗格正在显示如果窗格处于隐藏状态，则 FALSE。

### <a name="remarks"></a>备注

当显示或隐藏小型框架窗口中的窗格时，由框架调用。 默认实现不执行任何操作。

## <a name="cpaneframewndpin"></a><a name="pin"></a>CPaneFramewnd：:Pin

```cpp
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>参数

[在]*bPin*<br/>

### <a name="remarks"></a>备注

## <a name="cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CPaneFramewnd：:P从点

如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]用户单击的点，位于屏幕坐标中。

*nSensitivity*<br/>
[在]不使用此参数。

*b 检查可见性*<br/>
[在]TRUE 指定仅应返回可见窗格;否则，FALSE。

### <a name="return-value"></a>返回值

用户单击的窗格，如果该位置不存在窗格，则为 NULL。

### <a name="remarks"></a>备注

调用此方法以获取包含给定点的窗格。

## <a name="cpaneframewndredrawall"></a><a name="redrawall"></a>CPaneFramewnd：：重新绘制所有

重绘所有微型框架窗口。

```
static void RedrawAll();
```

### <a name="remarks"></a>备注

此方法通过为每个窗口调用[CWnd：：重新绘制窗口](../../mfc/reference/cwnd-class.md#redrawwindow)来更新所有微型框架窗口。

## <a name="cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CPaneFramed：：删除非有效窗格

由框架调用以删除非有效窗格。

```
virtual void RemoveNonValidPanes();
```

## <a name="cpaneframewndremovepane"></a><a name="removepane"></a>CPaneFramewnd：：删除窗格

从微型框架窗口删除窗格。

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向要删除的窗格的指针。

*b破坏*<br/>
[在]指定小型框架窗口发生的情况。 如果*b销毁*为 TRUE，则此方法将立即销毁微型框架窗口。 如果是 FALSE，则此方法在一定延迟后销毁微型框架窗口。

*b 无延迟销毁*<br/>
[在]如果为 TRUE，则禁用延迟销毁。 如果 FALSE，则启用延迟销毁。

### <a name="remarks"></a>备注

框架可以立即销毁微型框架窗口，也可以在一定延迟之后销毁。 如果要延迟对微型框架窗口的破坏，在*bNodelay 销毁*参数中传递 FALSE。 当框架处理AFX_WM_CHECKEMPTYMINIFRAME消息时，将发生延迟销毁。

## <a name="cpaneframewndreplacepane"></a><a name="replacepane"></a>CPaneFramewnd：：替换窗格

用一个窗格替换另一个窗格。

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>参数

*pBarOrg*<br/>
[在]指向原始窗格的指针。

*pbar 替换与*<br/>
[在]指向替换原始窗格的窗格的指针。

## <a name="cpaneframewndsavestate"></a><a name="savestate"></a>CPaneFramewnd：：保存状态

将窗格的状态保存到注册表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]配置文件名称。

*uiID*<br/>
[在]窗格 ID。

### <a name="return-value"></a>返回值

如果窗格状态已成功保存，则为 TRUE;如果窗格状态已成功保存，则为 TRUE。否则 FALSE。

## <a name="cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a>CPaneFramewnd：：设置标题按钮

设置标题按钮。

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>参数

*dwButtons*<br/>
[在]按位-OR 组合以下值：

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

## <a name="cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a>CPaneFramewnd：：设置延迟显示

```cpp
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>参数

[在]*bDelayShow*<br/>

### <a name="remarks"></a>备注

## <a name="cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a>CPaneFramewnd：：设置停靠管理器

```cpp
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>参数

[在]*p经理*<br/>

### <a name="remarks"></a>备注

## <a name="cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a>CPaneFramewnd：：设置停靠计时器

设置停靠计时器。

```cpp
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>参数

*nTimeOut*<br/>
[在]超时值（以毫秒为单位）。

## <a name="cpaneframewndsetdockstate"></a><a name="setdockstate"></a>CPaneFramewnd：：SetDockState

设置停靠状态。

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>参数

*pDock管理器*<br/>
[在]指向停靠管理器的指针。

## <a name="cpaneframewndsethotpoint"></a><a name="sethotpoint"></a>CPaneFramewnd：：设置HotPoint

```cpp
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>参数

[在]*pt New*<br/>

### <a name="remarks"></a>备注

## <a name="cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CPaneFramewnd：：设置PreDockstate

由框架调用以设置预停靠状态。

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>参数

*前DockState*<br/>
[在]可能的值：

- PDS_NOTHING

- PDS_DOCK_REGULAR

- PDS_DOCK_TO_TAB

*pBartodock*<br/>
[在]指向要停靠的窗格的指针。

*基方法*<br/>
[在]停靠方法。 （此参数将被忽略。

### <a name="return-value"></a>返回值

如果取消停靠，则为 TRUE;如果停靠了。"

## <a name="cpaneframewndsizetocontent"></a><a name="sizetocontent"></a>CPaneframed：：大小到内容

调整微型框架窗口的大小，使其等效于包含的窗格。

```
virtual void SizeToContent();
```

### <a name="remarks"></a>备注

调用此方法以将小型框架窗口的大小调整为包含窗格的大小。

## <a name="cpaneframewndstarttearoff"></a><a name="starttearoff"></a>CPaneFramewnd：：开始撕裂关闭

移走菜单。

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
[在]指向菜单的指针。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则，FALSE。

## <a name="cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneFramewnd：：存储最新网站信息

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneFramewnd：：存储最新标签相关信息

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>参数

[在]*pDockingBar*<br/>
[在]*pTabbedBar*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
