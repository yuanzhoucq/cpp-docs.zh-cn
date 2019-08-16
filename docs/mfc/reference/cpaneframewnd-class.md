---
title: CPaneFrameWnd 类
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
ms.openlocfilehash: 37ab241219f28336e73ea459a4e32ff413de8964
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502977"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd 类

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

实现包含一个窗格的微型框架窗口。 此窗格填满窗口的工作区。

## <a name="syntax"></a>语法

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
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
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|返回微型框架窗口标题的高度。|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|计算微型框架窗口标题的边框矩形。|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|返回标题文本。|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|返回停靠模式。|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|返回包含在微型框架窗口中的第一个可见窗格。|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|返回包含在微型框架窗口中的窗格。|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|返回包含在微型框架窗口中的窗格数。|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|返回包含在微型框架窗口中的可见窗格数。|
|[CPaneFrameWnd::HitTest](#hittest)|确定微型框架窗口的哪一部分位于给定点。|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|确定是否应下滚微型框架窗口。|
|[CPaneFrameWnd::IsRollUp](#isrollup)|确定是否应上滚微型框架窗口。|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|停止停靠计时器。|
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
|`CPaneFrameWnd::PreTranslateMessage`|在将窗口消息发送到 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) Windows 函数之前，由 [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) 类用于对此消息进行转换。|
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

|名称|描述|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|确定是否应上滚或下滚微型框架窗口。|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|绘制微型框架窗口的边框。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|指定是否注册 CS_SAVEBITS 类样式的窗口类。|

## <a name="remarks"></a>备注

当窗格从停靠状态切换到浮动状态时，框架会自动创建 `CPaneFrameWnd` 对象。

可使用其可见内容（立即停靠）或拖动矩形（标准停靠）来拖动微型框架窗口。 微型框架的容器窗格的停靠模式确定微型框架的拖动行为。 有关详细信息, 请参阅[CBasePane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)。

微型框架窗口根据包含的窗格样式在标题上显示按钮。 如果窗格可以关闭 ( [CBasePane:: CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), 它将显示 "关闭" 按钮。 如果窗格具有 AFX_CBRS_AUTO_ROLLUP 样式, 则会显示一个 pin。

如果从 `CPaneFrameWnd` 派生类，则必须告诉框架如何创建类。 可以通过重写[CPane:: CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)创建类, 也可以设置`CPane::m_pMiniFrameRTC`成员, 使其指向类的运行时类信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxPaneFrameWnd

##  <a name="addpane"></a>CPaneFrameWnd:: AddPane

添加窗格。

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中要添加的窗格。

##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd:: AddRemovePaneFromGlobalList

从全局列表添加或删除窗格。

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中要添加或删除的窗格。

*bAdd*<br/>
中如果非零, 则添加窗格。 如果为 0, 则删除窗格。

### <a name="return-value"></a>返回值

如果方法成功, 则为非零值;否则为0。

##  <a name="adjustlayout"></a>CPaneFrameWnd:: AdjustLayout

调整微型框架窗口的布局。

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>CPaneFrameWnd:: AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

##  <a name="calcbordersize"></a>CPaneFrameWnd:: CalcBorderSize

计算微型框窗口边框的大小。

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>参数

*rectBorderSize*<br/>
弄包含微型框窗口的边框的大小 (以像素为单位)。

### <a name="remarks"></a>备注

此方法由框架调用, 以计算微型框窗口边框的大小。 返回的大小取决于微型框窗口是包含工具栏还是[CDockablePane](../../mfc/reference/cdockablepane-class.md)。

##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd:: CalcExpectedDockedRect

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

*pWndToDock*<br/>
中指向要停靠的窗口的指针。

*ptMouse*<br/>
中鼠标位置。

*rectResult*<br/>
弄计算矩形。

*bDrawTab*<br/>
弄如果为 TRUE, 则绘制一个选项卡。如果为 FALSE, 则不绘制选项卡。

*ppTargetBar*<br/>
弄指向目标窗格的指针。

### <a name="remarks"></a>备注

如果用户将窗口拖动到*ptMouse*指定的点并将其停靠在该处, 此方法将计算窗口将占用的矩形。

##  <a name="canbeattached"></a>CPaneFrameWnd:: CanBeAttached

确定是否可将当前窗格停靠到另一个窗格或框架窗口。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

如果可以将窗格停靠到另一个窗格或框架窗口, 则为 TRUE;否则为 FALSE。

##  <a name="canbedockedtopane"></a>CPaneFrameWnd:: CanBeDockedToPane

确定是否可将微型框架窗口停靠到窗格。

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>参数

*pDockingBar*<br/>
中一个窗格。

### <a name="return-value"></a>返回值

如果迷你框架可停靠到*pDockingBar*, 则为非零值;否则为0。

##  <a name="checkgrippervisibility"></a>CPaneFrameWnd:: CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>备注

##  <a name="converttotabbeddocument"></a>CPaneFrameWnd:: ConvertToTabbedDocument

将窗格转换为选项卡式文档。

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>CPaneFrameWnd:: Create

创建微型框窗口并将其附加到[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)对象。

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*lpszWindowName*<br/>
中指定要在 "微型框" 窗口中显示的文本。

*dwStyle*<br/>
中指定窗口样式。 有关详细信息, 请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*rect*<br/>
中指定微型框窗口的初始大小和位置。

*pParentWnd*<br/>
[in, out]指定微型框窗口的父框架。 此值不得为 NULL。

*pContext*<br/>
[in, out]指定用户定义的上下文。

### <a name="return-value"></a>返回值

如果成功创建了窗口, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在两个步骤中, 将创建一个微型框窗口。 首先, 框架创建`CPaneFrameWnd`对象。 其次, 它调用`Create`创建 Windows 微型框窗口并将其附加`CPaneFrameWnd`到对象。

##  <a name="createex"></a>CPaneFrameWnd:: CreateEx

创建微型框窗口并将其附加到[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)对象。

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
中指定扩展的窗口样式。 有关详细信息, 请参阅[扩展的窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
中指定要在 "微型框" 窗口中显示的文本。

*dwStyle*<br/>
中指定窗口样式。 有关详细信息, 请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*rect*<br/>
中指定微型框窗口的初始大小和位置。

*pParentWnd*<br/>
[in, out]指定微型框窗口的父框架。 此值不得为 NULL。

*pContext*<br/>
[in, out]指定用户定义的上下文。

### <a name="return-value"></a>返回值

如果成功创建了窗口, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在两个步骤中, 将创建一个微型框窗口。 首先, 框架创建`CPaneFrameWnd`对象。 其次, 它调用`Create`创建 Windows 微型框窗口并将其附加`CPaneFrameWnd`到对象。

##  <a name="dockpane"></a>CPaneFrameWnd::D ockPane

停靠窗格。

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>参数

*bWasDocked*<br/>
弄如果已停靠该窗格, 则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

如果操作成功, `CDockablePane`则为窗格停靠到的; 否则为 NULL。

##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd:: FindFloatingPaneByID

在浮动窗格的全局列表中查找具有指定控件 ID 的窗格。

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
中表示要查找的窗格的控件 ID。

### <a name="return-value"></a>返回值

具有指定控件 ID 的窗格;否则, 如果没有窗格具有指定的控件 ID, 则为 NULL。

##  <a name="framefrompoint"></a>CPaneFrameWnd:: FrameFromPoint

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
中屏幕坐标中的点。

*nSensitivity*<br/>
中按此大小增大袖珍框架窗口的搜索区域。 如果给定点位于增加的区域, 则袖珍框架窗口满足搜索条件。

*pFrameToExclude*<br/>
中指定要从搜索中排除的微型框架窗口。

*bFloatMultiOnly*<br/>
中如果为 TRUE, 则仅搜索具有 CBRS_FLOAT_MULTI 样式的微型框架窗口。 如果为 FALSE, 则搜索所有微型框架窗口。

### <a name="return-value"></a>返回值

指向包含*pt*的袖珍框架窗口的指针;否则为 NULL。

##  <a name="getcaptionheight"></a>CPaneFrameWnd:: GetCaptionHeight

返回微型框架窗口标题的高度。

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>返回值

袖珍框架窗口的高度 (以像素为单位)。

### <a name="remarks"></a>备注

调用此方法以确定袖珍框架窗口的高度。 默认情况下, "高度" 设置为 "SM_CYSMCAPTION"。 有关详细信息, 请参阅[GetSystemMetrics 函数](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)。

##  <a name="getcaptionrect"></a>CPaneFrameWnd:: GetCaptionRect

计算微型框架窗口标题的边框矩形。

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>参数

*rectCaption*<br/>
弄包含袖珍框架窗口标题的大小和位置 (以屏幕坐标表示)。

### <a name="remarks"></a>备注

框架调用此方法来计算袖珍框架窗口标题的边框。

##  <a name="getcaptiontext"></a>CPaneFrameWnd:: GetCaptionText

返回标题文本。

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>返回值

袖珍框架窗口的标题文本。

### <a name="remarks"></a>备注

此方法在显示标题文本时由框架调用。

##  <a name="getdockingmanager"></a>CPaneFrameWnd:: GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getdockingmode"></a>CPaneFrameWnd:: GetDockingMode

返回停靠模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>返回值

停靠模式。 以下值之一：

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd:: GetFirstVisiblePane

返回包含在微型框架窗口中的第一个可见窗格。

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>返回值

微型框架窗口中的第一个窗格; 如果微型框架窗口不包含任何窗格, 则为 NULL。

##  <a name="gethotpoint"></a>CPaneFrameWnd:: GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpane"></a>CPaneFrameWnd:: GetPane

返回包含在微型框架窗口中的窗格。

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>返回值

小型框架中包含的窗格; 如果微型框架窗口不包含任何窗格, 则为 NULL。

### <a name="remarks"></a>备注

##  <a name="getpanecount"></a>CPaneFrameWnd:: GetPaneCount

返回包含在微型框架窗口中的窗格数。

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>返回值

袖珍框架窗口中窗格的数目。 此值可以为零。

### <a name="remarks"></a>备注

##  <a name="getparent"></a>CPaneFrameWnd:: GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpinstate"></a>CPaneFrameWnd:: GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd:: GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getvisiblepanecount"></a>CPaneFrameWnd:: GetVisiblePaneCount

返回包含在微型框架窗口中的可见窗格数。

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>返回值

可见窗格的数目。

### <a name="remarks"></a>备注

##  <a name="hittest"></a>CPaneFrameWnd:: System.windows.media.visualtreehelper.hittest

确定微型框架窗口的哪一部分位于给定点。

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>参数

*point*<br/>
中要测试的点。

*bDetectCaption*<br/>
中如果为 TRUE, 则检查标题上的点。 如果为 FALSE, 则忽略标题。

### <a name="return-value"></a>返回值

以下值之一：

|值|含义|
|-----------|-------------|
|HTNOWHERE|点在袖珍框架窗口之外。|
|HTCLIENT|点在工作区中。|
|HTCAPTION|点在标题上。|
|HTTOP|点位于顶部。|
|HTTOPLEFT|点位于左上角。|
|HTTOPRIGHT|点在右上角。|
|HTLEFT|点位于左侧。|
|HTRIGHT|点位于右侧。|
|HTBOTTOM|点位于底部。|
|HTBOTTOMLEFT|点在左下角。|
|HTBOTTOMRIGHT|点位于右下方。|

##  <a name="iscaptured"></a>CPaneFrameWnd:: IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isdelayshow"></a>CPaneFrameWnd:: IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isrolldown"></a>CPaneFrameWnd:: IsRollDown

确定是否应下滚微型框架窗口。

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>返回值

如果必须向下滚动袖珍框架窗口, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法由框架调用, 以确定是否应向下滚动袖珍框架窗口。 如果在小型框架窗口中至少包含一个具有 AFX_CBRS_AUTO_ROLLUP 标志的窗格, 则为其启用 rollup/rolldown 功能。 创建窗格时将设置此标志。 有关详细信息, 请参阅[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)。

默认情况下, 框架检查鼠标指针是否位于袖珍框架窗口边框内, 以确定是否必须向下滚动窗口。 可以在派生类中重写此行为。

##  <a name="isrollup"></a>CPaneFrameWnd:: IsRollUp

确定是否应上滚微型框架窗口。

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>返回值

如果必须汇总袖珍框架窗口, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法由框架调用, 以确定是否应汇总微型框架窗口。 如果在小型框架窗口中至少包含一个具有 AFX_CBRS_AUTO_ROLLUP 标志的窗格, 则为其启用 rollup/rolldown 功能。 创建窗格时将设置此标志。 有关详细信息, 请参阅[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)。

默认情况下, 框架检查鼠标指针是否位于袖珍框架窗口边界矩形内, 以确定是否必须汇总该窗口。 可以在派生类中重写此行为。

##  <a name="killdockingtimer"></a>CPaneFrameWnd:: KillDockingTimer

停止停靠计时器。

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>CPaneFrameWnd:: LoadState

从注册表加载窗格的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中配置文件名称。

*uiID*<br/>
中窗格 ID。

### <a name="return-value"></a>返回值

如果成功加载了窗格状态, 则为 TRUE;否则为 FALSE。

##  <a name="m_busesavebits"></a>CPaneFrameWnd:: m_bUseSaveBits

指定是否注册具有 CS_SAVEBITS 类样式的窗口类。

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>备注

将此静态成员设置为 TRUE, 以注册具有 CS_SAVEBITS 样式的袖珍框架窗口类。 当用户拖动微型框架窗口时, 这有助于减少闪烁。

##  <a name="onbeforedock"></a>CPaneFrameWnd:: OnBeforeDock

确定停靠是否可能。

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>返回值

如果可以进行停靠, 则为 TRUE;否则为 FALSE。

##  <a name="oncheckrollstate"></a>CPaneFrameWnd:: OnCheckRollState

确定是否应上滚或下滚微型框架窗口。

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>备注

此方法由框架调用, 以确定是否应向上或向下滚动袖珍框架窗口。

默认情况下, 框架将调用[CPaneFrameWnd:: IsRollUp](#isrollup)和[CPaneFrameWnd:: IsRollDown](#isrolldown) , 并只拉伸或还原袖珍框架窗口。 可以在派生类中重写此方法, 以使用不同的视觉效果。

##  <a name="ondocktorecentpos"></a>CPaneFrameWnd:: OnDockToRecentPos

将微型框架窗口停靠在其最新的位置。

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>CPaneFrameWnd:: OnDrawBorder

绘制微型框架窗口的边框。

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中用于绘制边框的设备上下文。

### <a name="remarks"></a>备注

框架调用此方法来绘制袖珍框架窗口的边框。

##  <a name="onkillrolluptimer"></a>CPaneFrameWnd:: OnKillRollUpTimer

停止汇总计时器。

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>CPaneFrameWnd:: OnMovePane

按指定偏移量移动微型框架窗口。

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>参数

*pBar*<br/>
中指向窗格的指针 (已忽略)。

*ptOffset*<br/>
中用于移动窗格的偏移量。

##  <a name="onpanerecalclayout"></a>CPaneFrameWnd:: OnPaneRecalcLayout

调整小型框架窗口中窗格的布局。

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>备注

当框架必须调整微型框架窗口中窗格的布局时, 框架会调用此方法。

默认情况下, 窗格定位以覆盖袖珍框架窗口的整个工作区。

##  <a name="onsetrolluptimer"></a>CPaneFrameWnd:: OnSetRollUpTimer

设置汇总计时器。

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>CPaneFrameWnd:: OnShowPane

隐藏或显示微型框架窗口的窗格时，由框架进行调用。

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>参数

*pBar*<br/>
中正在显示或隐藏的窗格。

*bShow*<br/>
中如果正在显示窗格, 则为 TRUE;如果该窗格处于隐藏状态, 则为 FALSE。

### <a name="remarks"></a>备注

当显示或隐藏微型框架窗口中的窗格时由框架调用。 默认实现不执行任何操作。

##  <a name="pin"></a>CPaneFrameWnd::P

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>参数

中*bPin*<br/>

### <a name="remarks"></a>备注

##  <a name="panefrompoint"></a>CPaneFrameWnd::P aneFromPoint

如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>参数

*point*<br/>
中用户单击的屏幕坐标中的点。

*nSensitivity*<br/>
中未使用此参数。

*bCheckVisibility*<br/>
中若要指定仅返回可见窗格, 则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

用户单击的窗格; 如果该位置不存在任何窗格, 则为 NULL。

### <a name="remarks"></a>备注

调用此方法以获取包含给定点的窗格。

##  <a name="redrawall"></a>CPaneFrameWnd:: RedrawAll

重绘所有微型框架窗口。

```
static void RedrawAll();
```

### <a name="remarks"></a>备注

此方法通过对每个窗口调用[CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)来更新所有微型框架窗口。

##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes

由框架调用以删除非有效窗格。

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>CPaneFrameWnd:: RemovePane

从微型框架窗口删除窗格。

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向要删除的窗格的指针。

*bDestroy*<br/>
中指定袖珍框架窗口发生的情况。 如果*bDestroy*为 TRUE, 则此方法会立即销毁微型框架窗口。 如果此方法为 FALSE, 则此方法在一定延迟后会销毁微型框架窗口。

*bNoDelayedDestroy*<br/>
中如果为 TRUE, 则禁用延迟的析构。 如果为 FALSE, 则启用延迟的析构。

### <a name="remarks"></a>备注

框架可以立即销毁袖珍框架窗口, 也可以在某个延迟之后销毁。 如果要延迟袖珍框架窗口的销毁, 请在*bNoDelayedDestroy*参数中传递 FALSE。 当框架处理 AFX_WM_CHECKEMPTYMINIFRAME 消息时, 将发生延迟的析构。

##  <a name="replacepane"></a>CPaneFrameWnd:: ReplacePane

用一个窗格替换另一个窗格。

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>参数

*pBarOrg*<br/>
中指向原始窗格的指针。

*pBarReplaceWith*<br/>
中指向替换原始窗格的窗格的指针。

##  <a name="savestate"></a>CPaneFrameWnd:: SaveState

将窗格的状态保存到注册表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中配置文件名称。

*uiID*<br/>
中窗格 ID。

### <a name="return-value"></a>返回值

如果成功保存窗格状态, 则为 TRUE;否则为 FALSE。

##  <a name="setcaptionbuttons"></a>CPaneFrameWnd:: SetCaptionButtons

设置标题按钮。

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>参数

*dwButtons*<br/>
中以下值的按位 "或" 组合:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>CPaneFrameWnd:: SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>参数

[in] *bDelayShow*<br/>

### <a name="remarks"></a>备注

##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>参数

[in] *pManager*<br/>

### <a name="remarks"></a>备注

##  <a name="setdockingtimer"></a>CPaneFrameWnd:: SetDockingTimer

设置停靠计时器。

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>参数

*nTimeOut*<br/>
中超时值 (以毫秒为单位)。

##  <a name="setdockstate"></a>CPaneFrameWnd:: SetDockState

设置停靠状态。

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>参数

*pDockManager*<br/>
中指向停靠管理器的指针。

##  <a name="sethotpoint"></a>CPaneFrameWnd:: SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>参数

[in] *ptNew*<br/>

### <a name="remarks"></a>备注

##  <a name="setpredockstate"></a>CPaneFrameWnd:: SetPreDockState

由框架调用以设置预停靠状态。

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>参数

*preDockState*<br/>
中可能的值:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
中指向要停靠的窗格的指针。

*dockMethod*<br/>
中停靠方法。 (忽略此参数。)

### <a name="return-value"></a>返回值

如果未停靠袖珍框架窗口, 则为 TRUE;如果已停靠, 则为 FALSE。

##  <a name="sizetocontent"></a>CPaneFrameWnd:: System.windows.window.sizetocontent

调整微型框架窗口的大小, 使其等效于包含的窗格。

```
virtual void SizeToContent();
```

### <a name="remarks"></a>备注

调用此方法可将袖珍框架窗口的大小调整为包含窗格的大小。

##  <a name="starttearoff"></a>CPaneFrameWnd:: StartTearOff

移走菜单。

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
中指向菜单的指针。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="storerecentdocksiteinfo"></a>CPaneFrameWnd:: StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

中*pBar*<br/>

### <a name="remarks"></a>备注

##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd:: StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>参数

[in] *pDockingBar*<br/>
中*pTabbedBar*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
