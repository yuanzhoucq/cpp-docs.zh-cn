---
title: CPaneFrameWnd 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34ac2ddb08b485a56274f6067871c5bbd5893f94
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434812"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd 类

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

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
|`CPaneFrameWnd::PreTranslateMessage`|类使用[CWinApp](../../mfc/reference/cwinapp-class.md)窗口消息调度到之前转换[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)并[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。|
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

|name|描述|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|指定是否将窗口类注册 CS_SAVEBITS 类样式。|

## <a name="remarks"></a>备注

当窗格从停靠状态切换到浮动状态时，框架会自动创建 `CPaneFrameWnd` 对象。

可使用其可见内容（立即停靠）或拖动矩形（标准停靠）来拖动微型框架窗口。 微型框架的容器窗格的停靠模式确定微型框架的拖动行为。 有关详细信息，请参阅[cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode)。

微型框架窗口根据包含的窗格样式在标题上显示按钮。 如果可以关闭窗格 ( [cbasepane:: Canbeclosed](../../mfc/reference/cbasepane-class.md#canbeclosed))，它将显示关闭按钮。 如果窗格具有 AFX_CBRS_AUTO_ROLLUP 样式，它将显示指针。

如果从 `CPaneFrameWnd` 派生类，则必须告诉框架如何创建类。 通过重写创建类[cpane:: Createdefaultminiframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)，或设置`CPane::m_pMiniFrameRTC`成员使其指向您的类的运行时类信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>要求

**标头：** afxPaneFrameWnd.h

##  <a name="addpane"></a>  CPaneFrameWnd::AddPane

添加窗格。

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in]要添加的窗格。

##  <a name="addremovepanefromgloballist"></a>  CPaneFrameWnd::AddRemovePaneFromGlobalList

从全局列表添加或删除窗格。

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in]若要添加或删除窗格。

*b 将*<br/>
[in]如果非零，则添加窗格。 如果为 0，则删除窗格。

### <a name="return-value"></a>返回值

如果此方法已成功，则非零值否则为 0。

##  <a name="adjustlayout"></a>  CPaneFrameWnd::AdjustLayout

调整微型框架窗口的布局。

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>  CPaneFrameWnd::AdjustPaneFrames


```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>备注

##  <a name="calcbordersize"></a>  CPaneFrameWnd::CalcBorderSize

计算微型框窗口的边框的大小。

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>参数

*rectBorderSize*<br/>
[out]包含以像素为单位的微型框窗口边框的大小。

### <a name="remarks"></a>备注

若要计算的袖珍框架窗口的边框的大小的框架调用此方法。 返回的大小取决于是否袖珍框架窗口包含一个工具栏或[CDockablePane](../../mfc/reference/cdockablepane-class.md)。

##  <a name="calcexpecteddockedrect"></a>  CPaneFrameWnd::CalcExpectedDockedRect

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
[in]指向窗口停靠的指针。

*ptMouse*<br/>
[in]鼠标位置。

*rectResult*<br/>
[out]计算的矩形。

*bDrawTab*<br/>
[out]如果为 TRUE，绘制选项卡。如果为 FALSE，则不会绘制一个选项卡。

*ppTargetBar*<br/>
[out]指向目标窗格的指针。

### <a name="remarks"></a>备注

此方法计算一个窗口，如果用户将窗口拖到由指定的点会占用的矩形*ptMouse*和那里停靠。

##  <a name="canbeattached"></a>  CPaneFrameWnd::CanBeAttached

确定是否可将当前窗格停靠到另一个窗格或框架窗口。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

可将窗格停靠到另一个窗格或框架窗口; 如果为 TRUE否则为 FALSE。

##  <a name="canbedockedtopane"></a>  CPaneFrameWnd::CanBeDockedToPane

确定是否可将微型框架窗口停靠到窗格。

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>参数

*pDockingBar*<br/>
[in]一个窗格。

### <a name="return-value"></a>返回值

如果微型框架可停靠到非零*pDockingBar*; 否则为 0。

##  <a name="checkgrippervisibility"></a>  CPaneFrameWnd::CheckGripperVisibility


```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>备注

##  <a name="converttotabbeddocument"></a>  CPaneFrameWnd::ConvertToTabbedDocument

将窗格转换为选项卡式文档。

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>  CPaneFrameWnd::Create

创建微型框窗口，并将其附加到[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)对象。

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
[in]指定要在袖珍框架窗口上显示的文本。

*dwStyle*<br/>
[in]指定的窗口样式。 有关详细信息，请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*rect*<br/>
[in]指定的初始大小和袖珍框架窗口的位置。

[in][out]*pParentWnd*指定袖珍框架窗口的父框架。 此值不能为 NULL。

[in][out]*pContext*指定用户定义的上下文。

### <a name="return-value"></a>返回值

如果该窗口已创建的成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

在两个步骤中将创建一个微型框窗口。 首先，框架将创建`CPaneFrameWnd`对象。 其次，它将调用`Create`若要创建 Windows 微型框窗口，并将其附加到`CPaneFrameWnd`对象。

##  <a name="createex"></a>  CPaneFrameWnd::CreateEx

创建微型框窗口，并将其附加到[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)对象。

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
[in]指定扩展的窗口样式。 有关详细信息，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
[in]指定要在袖珍框架窗口上显示的文本。

*dwStyle*<br/>
[in]指定的窗口样式。 有关详细信息，请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*rect*<br/>
[in]指定的初始大小和袖珍框架窗口的位置。

[in][out]*pParentWnd*指定袖珍框架窗口的父框架。 此值不能为 NULL。

[in][out]*pContext*指定用户定义的上下文。

### <a name="return-value"></a>返回值

如果该窗口已创建的成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

在两个步骤中将创建一个微型框窗口。 首先，框架将创建`CPaneFrameWnd`对象。 其次，它将调用`Create`若要创建 Windows 微型框窗口，并将其附加到`CPaneFrameWnd`对象。

##  <a name="dockpane"></a>  CPaneFrameWnd::DockPane

停靠窗格。

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>参数

*bWasDocked*<br/>
[out]如果已停靠窗格; 则为 TRUE否则为 FALSE。

### <a name="return-value"></a>返回值

如果操作成功，`CDockablePane`窗格是停靠到; 否则为 NULL。

##  <a name="findfloatingpanebyid"></a>  CPaneFrameWnd::FindFloatingPaneByID

在浮动窗格的全局列表中查找具有指定控件 ID 的窗格。

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
[in]表示要查找窗格的控件 ID。

### <a name="return-value"></a>返回值

具有指定的控件 ID; 窗格否则为 NULL，如果没有窗格会显示指定的控件 id。

##  <a name="framefrompoint"></a>  CPaneFrameWnd::FrameFromPoint

查找包含指定的点的微型框架窗口。

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>参数

*pt*<br/>
[in]屏幕坐标中的点。

*nSensitivity*<br/>
[in]通过此大小增加微型框架窗口的搜索区域。 如果给的定点落在更高的区域，微型框架窗口将满足搜索条件。

*pFrameToExclude*<br/>
[in]指定要从搜索中排除的微型框架窗口。

*bFloatMultiOnly*<br/>
[in]如果为 TRUE，仅搜索已 CBRS_FLOAT_MULTI 样式的微型框架窗口。 如果为 FALSE，搜索所有微型框架窗口。

### <a name="return-value"></a>返回值

指向包含在微型框架窗口的指针*pt*; 否则为 NULL。

##  <a name="getcaptionheight"></a>  CPaneFrameWnd::GetCaptionHeight

返回微型框架窗口标题的高度。

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>返回值

以像素为单位的微型框架窗口的高度。

### <a name="remarks"></a>备注

调用此方法来确定微型框架窗口的高度。 默认情况下，高度设置为 SM_CYSMCAPTION。 有关详细信息，请参阅[GetSystemMetrics 函数](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics)。

##  <a name="getcaptionrect"></a>  CPaneFrameWnd::GetCaptionRect

计算微型框架窗口标题的边框矩形。

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>参数

*rectCaption*<br/>
[out]包含的大小和屏幕坐标中的微型框架窗口标题的位置。

### <a name="remarks"></a>备注

若要计算微型框架窗口标题的边框的框架调用此方法。

##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText

返回标题文本。

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>返回值

微型框架窗口的标题文本。

### <a name="remarks"></a>备注

显示的标题文本时，由框架调用此方法。

##  <a name="getdockingmanager"></a>  CPaneFrameWnd::GetDockingManager


```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getdockingmode"></a>  CPaneFrameWnd::GetDockingMode

返回停靠模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>返回值

停靠模式。 以下值之一：

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>  CPaneFrameWnd::GetFirstVisiblePane

返回包含在微型框架窗口中的第一个可见窗格。

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>返回值

中的微型框架窗口中或如果微型框架窗口不包含任何窗格，则为 NULL 的第一个窗格。

##  <a name="gethotpoint"></a>  CPaneFrameWnd::GetHotPoint


```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpane"></a>  CPaneFrameWnd::GetPane

返回包含在微型框架窗口中的窗格。

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>返回值

如果微型框架窗口不包含任何窗格包含在微型框架或为空的窗格。

### <a name="remarks"></a>备注

##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount

返回包含在微型框架窗口中的窗格数。

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>返回值

微型框架窗口中的窗格数。 此值可以为零。

### <a name="remarks"></a>备注

##  <a name="getparent"></a>  CPaneFrameWnd::GetParent


```
CWnd* GetParent();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpinstate"></a>  CPaneFrameWnd::GetPinState


```
BOOL GetPinState() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecentfloatingrect"></a>  CPaneFrameWnd::GetRecentFloatingRect


```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getvisiblepanecount"></a>  CPaneFrameWnd::GetVisiblePaneCount

返回包含在微型框架窗口中的可见窗格数。

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>返回值

可见窗格数。

### <a name="remarks"></a>备注

##  <a name="hittest"></a>  CPaneFrameWnd::HitTest

确定微型框架窗口的哪一部分位于给定点。

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>参数

*点*<br/>
[in]要测试的点。

*bDetectCaption*<br/>
[in]如果为 TRUE，则检查针对标题的点。 如果为 FALSE，则忽略标题。

### <a name="return-value"></a>返回值

以下值之一：

|“值”|含义|
|-----------|-------------|
|HTNOWHERE|关键是微型框架窗口外。|
|HTCLIENT|关键是工作区中。|
|HTCAPTION|关键是在标题上。|
|HTTOP|点位于顶部。|
|HTTOPLEFT|在点位于左上角。|
|HTTOPRIGHT|在右上角点。|
|HTLEFT|在点位于左侧。|
|HTRIGHT|点位于右侧。|
|HTBOTTOM|点位于底部。|
|HTBOTTOMLEFT|在左下角点。|
|HTBOTTOMRIGHT|在点位于靠下右对齐。|

##  <a name="iscaptured"></a>  CPaneFrameWnd::IsCaptured


```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isdelayshow"></a>  CPaneFrameWnd::IsDelayShow


```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isrolldown"></a>  CPaneFrameWnd::IsRollDown

确定是否应下滚微型框架窗口。

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>返回值

如果必须向; 下滚微型框架窗口，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

若要确定是否应下滚微型框架窗口的框架调用此方法。 如果它包含至少一个 AFX_CBRS_AUTO_ROLLUP 标志的窗格中，将微型框架窗口启用下滚汇总/功能。 创建一个窗格时，设置此标志。 有关详细信息，请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。

默认情况下，框架将检查鼠标指针是否位于微型框架窗口边界矩形来确定窗口是否具有要下滚。 您可以重写此行为在派生类中。

##  <a name="isrollup"></a>  CPaneFrameWnd::IsRollUp

确定是否应上滚微型框架窗口。

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>返回值

如果必须汇总微型框架窗口; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

确定是否应汇总微型框架窗口的框架调用此方法。 如果它包含至少一个 AFX_CBRS_AUTO_ROLLUP 标志的窗格中，将微型框架窗口启用下滚汇总/功能。 创建一个窗格时，设置此标志。 有关详细信息，请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。

默认情况下，框架检查鼠标指针是否位于微型框架窗口边界矩形来确定窗口是否具有要进行汇总。 您可以重写此行为在派生类中。

##  <a name="killdockingtimer"></a>  CPaneFrameWnd::KillDockingTimer

停止停靠计时器。

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>  CPaneFrameWnd::LoadState

从注册表加载窗格的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
[in]配置文件名称。

*uiID*<br/>
[in]窗格 id。

### <a name="return-value"></a>返回值

如果窗格状态加载成功，则为 TRUE否则为 FALSE。

##  <a name="m_busesavebits"></a>  CPaneFrameWnd::m_bUseSaveBits

指定是否注册具有 CS_SAVEBITS 类样式的窗口类。

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>备注

设置为 true，则具有 CS_SAVEBITS 样式的微型框架窗口类注册到此静态成员。 这可能有助于减少闪烁时在用户拖动微型框架窗口。

##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock

确定停靠是否可能。

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>返回值

停靠; 如果为 TRUE否则为 FALSE。

##  <a name="oncheckrollstate"></a>  CPaneFrameWnd::OnCheckRollState

确定是否应上滚或下滚微型框架窗口。

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>备注

若要确定是否应向上或向下滚微型框架窗口的框架调用此方法。

默认情况下，框架将调用[CPaneFrameWnd::IsRollUp](#isrollup)并[CPaneFrameWnd::IsRollDown](#isrolldown)只拉伸或还原微型框架窗口。 您可以重写此方法在派生类以使用不同的可视化效果中。

##  <a name="ondocktorecentpos"></a>  CPaneFrameWnd::OnDockToRecentPos

将微型框架窗口停靠在其最新的位置。

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>  CPaneFrameWnd::OnDrawBorder

绘制微型框架窗口的边框。

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]用于绘制边框的设备上下文。

### <a name="remarks"></a>备注

若要绘制微型框架窗口的边框的框架调用此方法。

##  <a name="onkillrolluptimer"></a>  CPaneFrameWnd::OnKillRollUpTimer

停止汇总计时器。

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>  CPaneFrameWnd::OnMovePane

按指定偏移量移动微型框架窗口。

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in]指向一个窗格 （忽略） 的指针。

*ptOffset*<br/>
[in]要将窗格移动偏移量。

##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout

调整微型框架窗口中窗格的布局。

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>备注

它必须调整微型框架窗口中窗格的布局时，框架将调用此方法。

默认情况下，窗格中定位来覆盖微型框架窗口的完整的客户端区域。

##  <a name="onsetrolluptimer"></a>  CPaneFrameWnd::OnSetRollUpTimer

设置汇总计时器。

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>  CPaneFrameWnd::OnShowPane

隐藏或显示微型框架窗口的窗格时，由框架进行调用。

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in]在窗格中显示或隐藏。

*bShow*<br/>
[in]所显示的窗格中; 如果为 TRUE如果要隐藏窗格，则为 FALSE。

### <a name="remarks"></a>备注

显示或隐藏窗格在微型框架窗口时由框架调用。 默认实现不执行任何操作。

##  <a name="pin"></a>  CPaneFrameWnd::Pin


```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>参数

[in]*bPin*

### <a name="remarks"></a>备注

##  <a name="panefrompoint"></a>  CPaneFrameWnd::PaneFromPoint

如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>参数

*点*<br/>
[in]点用户单击以屏幕坐标表示。

*nSensitivity*<br/>
[in]未使用此参数。

*bCheckVisibility*<br/>
[in]为 TRUE，则指定应返回仅可见窗格;否则为 FALSE。

### <a name="return-value"></a>返回值

窗格中，用户单击或如果该位置不存在任何窗格，则为 NULL。

### <a name="remarks"></a>备注

调用此方法来获得一个窗格，其中包含给定的点。

##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll

重绘所有微型框架窗口。

```
static void RedrawAll();
```

### <a name="remarks"></a>备注

此方法通过调用来更新所有微型框架窗口[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)为每个窗口。

##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes

由框架调用以删除非有效窗格。

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>  CPaneFrameWnd::RemovePane

从微型框架窗口删除窗格。

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in]指向要删除的窗格的指针。

*bDestroy*<br/>
[in]指定到微型框架窗口的操作。 如果*bDestroy*为 TRUE 时，此方法将立即销毁微型框架窗口。 如果为 FALSE，则此方法在某些延迟之后销毁微型框架窗口。

*bNoDelayedDestroy*<br/>
[in]如果为 TRUE，则禁用延迟的析构。 如果为 FALSE，则启用延迟的析构。

### <a name="remarks"></a>备注

立即或在某些延迟之后，该框架可以销毁微型框架窗口。 如果你想要延迟析构的微型框架窗口，将传递 FALSE *bNoDelayedDestroy*参数。 框架处理 AFX_WM_CHECKEMPTYMINIFRAME 消息时出现延迟的析构。

##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane

用一个窗格替换另一个窗格。

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>参数

*pBarOrg*<br/>
[in]指向原始的窗格的指针。

*pBarReplaceWith*<br/>
[in]指向将替换原始窗格的窗格的指针。

##  <a name="savestate"></a>  CPaneFrameWnd::SaveState

将窗格的状态保存到注册表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
[in]配置文件名称。

*uiID*<br/>
[in]窗格 id。

### <a name="return-value"></a>返回值

如果窗格状态已保存成功，则为 TRUE否则为 FALSE。

##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons

设置标题按钮。

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>参数

*dwButtons*<br/>
[in]以下值的按位 OR 组合：

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow


```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>参数

[in]*bDelayShow*

### <a name="remarks"></a>备注

##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager


```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>参数

[in]*pManager*

### <a name="remarks"></a>备注

##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer

设置停靠计时器。

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>参数

*nTimeOut*<br/>
[in]以毫秒为单位的超时值。

##  <a name="setdockstate"></a>  CPaneFrameWnd::SetDockState

设置停靠状态。

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>参数

*pDockManager*<br/>
[in]停靠管理器指向的指针。

##  <a name="sethotpoint"></a>  CPaneFrameWnd::SetHotPoint


```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>参数

[in]*ptNew*

### <a name="remarks"></a>备注

##  <a name="setpredockstate"></a>  CPaneFrameWnd::SetPreDockState

由框架调用以设置预停靠状态。

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>参数

*preDockState*<br/>
[in]可能的值：

- PDS_NOTHING，

- PDS_DOCK_REGULAR，

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
[in]指向要停靠的窗格的指针。

*dockMethod*<br/>
[in]停靠的方法。 （忽略此参数。）

### <a name="return-value"></a>返回值

微型框架窗口停靠; 如果为 TRUE如果为 FALSE。

##  <a name="sizetocontent"></a>  CPaneFrameWnd::SizeToContent

调整微型框架窗口的大小，使它等效于包含的窗格。

```
virtual void SizeToContent();
```

### <a name="remarks"></a>备注

调用此方法以调整微型框架窗口包含窗格的大小的大小。

##  <a name="starttearoff"></a>  CPaneFrameWnd::StartTearOff

移走菜单。

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
[in]指向一个菜单的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo


```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

[in]*pBar*

### <a name="remarks"></a>备注

##  <a name="storerecenttabrelatedinfo"></a>  CPaneFrameWnd::StoreRecentTabRelatedInfo


```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>参数

*pDockingBar*<br/>
[in][in]*pTabbedBar*

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
