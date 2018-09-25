---
title: CDockSite 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
dev_langs:
- C++
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd3af20ecc4639a4a48f8fd7f9040a1f18fd34fb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386948"
---
# <a name="cdocksite-class"></a>CDockSite Class

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

提供用于排列从 [CPane Class](../../mfc/reference/cpane-class.md) 派生至多组行的窗格的功能。

## <a name="syntax"></a>语法

```
class CDockSite: public CBasePane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(重写[cbasepane:: Adjustdockinglayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)。)|
|[CDockSite::AdjustLayout](#adjustlayout)|(重写[cbasepane:: Adjustlayout](../../mfc/reference/cbasepane-class.md#adjustlayout)。)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(重写[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(重写[cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane)。)|
|[CDockSite::CreateEx](#createex)|(重写[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(重写[cbasepane:: Dockpane](../../mfc/reference/cbasepane-class.md#dockpane)。)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(重写[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|（重写 `CBasePane::IsAccessibilityCompatible`。）|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(重写[cbasepane:: Isresizable](../../mfc/reference/cbasepane-class.md#isresizable)。)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|返回在停靠站点中给定参数指定的点处停靠的窗格。|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|将窗格停靠到另一个窗格的左侧。|
|[CDockSite::FindPaneByID](#findpanebyid)|返回由给定 ID 标识的窗格。|
|[CDockSite::GetPaneList](#getpanelist)|返回停靠在停靠站点的窗格列表。|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|显示窗格。|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>备注

框架将创建`CDockSite`对象自动调用时[cframewndex:: Enabledocking](../../mfc/reference/cframewndex-class.md#enabledocking)。 停靠站点窗口位于主框架窗口上的工作区边缘。

通常不需要调用因为由停靠站点提供的服务[CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)会处理这些服务。

## <a name="example"></a>示例

下面的示例演示如何创建 `CDockSite` 类的对象。

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>要求

**标头：** afxDockSite.h

##  <a name="addrow"></a>  CDockSite::AddRow


```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>参数

*pos*<br/>
[in][in]*nHeight*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout


```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>备注

##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout


```
virtual void AdjustLayout();
```

### <a name="remarks"></a>备注

##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite


```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>参数

*rectToAlignBy*<br/>
[in][in]*rectResult* [in] *bMoveImmediately*

### <a name="remarks"></a>备注

##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout


```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*bStretch*<br/>
[in][in]*bHorz*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane


```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>参数

[in]*pBar*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="createex"></a>  CDockSite::CreateEx


```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*dwStyleEx*<br/>
[in][in]*dwStyle*
*rect*<br/>
[in][in]*pParentWnd*
*dwControlBarStyle*<br/>
[in][in]*pContext*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="createrow"></a>  CDockSite::CreateRow


```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>参数

*pParentDockBar*<br/>
[in][in]*nOffset* [in] *nRowHeight*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="dockpane"></a>  CDockSite::DockPane


```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in][in]*dockMethod* [in] *lpRect*

### <a name="remarks"></a>备注

##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf

将窗格停靠到另一个窗格的左侧。

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>参数

[in][out]*pBarToDock*指向左侧的停靠窗格*pTargetBar*。

[in][out]*pTargetBar*到目标窗格的指针。

### <a name="return-value"></a>返回值

如果成功，则停靠窗格，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore


```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="findpanebyid"></a>  CDockSite::FindPaneByID

返回与给定 ID 的窗格

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
[in]要找到窗格中的命令 ID。

### <a name="return-value"></a>返回值

指向与指定的命令 ID 或如果找不到窗格中，则为 NULL 的窗格的指针。

### <a name="remarks"></a>备注

##  <a name="findrowindex"></a>  CDockSite::FindRowIndex


```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>参数

[in]*pRow*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects


```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>备注

##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID


```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList


```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpanelist"></a>  CDockSite::GetPaneList

返回在停靠站点停靠的窗格的列表。

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>返回值

对的窗格的列表的只读引用当前停靠在停靠栏中。

##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible


```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isdragmode"></a>  CDockSite::IsDragMode


```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="islastrow"></a>  CDockSite::IsLastRow


```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>参数

[in]*pRow*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite


```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in][in]*ptDelta*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isresizable"></a>  CDockSite::IsResizable


```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="movepane"></a>  CDockSite::MovePane


```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in][in]*nFlags* [in] *ptOffset*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow


```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>参数

[in]*pos*

### <a name="remarks"></a>备注

##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow


```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>参数

*pos*<br/>
[in][in]*bByShow*

### <a name="remarks"></a>备注

##  <a name="onresizerow"></a>  CDockSite::OnResizeRow


```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>参数

*pRowToResize*<br/>
[in][in]*nOffset*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onsizeparent"></a>  CDockSite::OnSizeParent


```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>参数

*rectAvailable*<br/>
[in][in]*深入剖析*
*bExpand*<br/>
[in][in]*nOffset*

### <a name="remarks"></a>备注

##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos


```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*pWndInsertAfter*<br/>
[in][in]*rectWnd* [in] *nFlags*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onshowrow"></a>  CDockSite::OnShowRow


```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>参数

*pos*<br/>
[in][in]*bShow*

### <a name="remarks"></a>备注

##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint

返回在停靠站点中给定参数指定的点处停靠的窗格。

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
[in]屏幕坐标，若要检索的窗格中的点。

### <a name="return-value"></a>返回值

指向位于指定的点或为 NULL，如果没有窗格是位于指定点的窗格的指针。

### <a name="remarks"></a>备注

##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint


```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in][in]*点*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="removepane"></a>  CDockSite::RemovePane


```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in][in]*dockMethod*

### <a name="remarks"></a>备注

##  <a name="removerow"></a>  CDockSite::RemoveRow


```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>参数

[in]*pRow*

### <a name="remarks"></a>备注

##  <a name="replacepane"></a>  CDockSite::ReplacePane


```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>参数

*pOldBar*<br/>
[in][in]*pNewBar*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes


```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>参数

[in]*rectNewClientArea*

### <a name="remarks"></a>备注

##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite


```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>参数

*nNewWidth*<br/>
[in][in]*nNewHeight*

### <a name="remarks"></a>备注

##  <a name="resizerow"></a>  CDockSite::ResizeRow


```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>参数

*pRow*<br/>
[in][in]*nNewSize* [in] *bAdjustLayout*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="showpane"></a>  CDockSite::ShowPane

显示窗格。

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>参数

[in][out]*pBar*指向窗格是显示还是隐藏的。

*bShow*<br/>
[in]若要指定要显示; 窗格中，则返回 TRUE如果为 FALSE，来指定要隐藏窗格。

*bDelay*<br/>
[in]若要指定显示在窗格; 后应直到延迟窗格的布局，则返回 TRUE否则为 FALSE。

*bActivate*<br/>
[in]未使用此参数。

### <a name="return-value"></a>返回值

如果窗格是显示还是隐藏成功，则为 TRUE。 如果指定的窗格中不属于此停靠站点，则为 FALSE。

### <a name="remarks"></a>备注

调用此方法以显示或隐藏停靠的窗格。 通常情况下，不需要调用`CDockSite::ShowPane`直接，因为它调用通过父框架窗口或基本窗格。

##  <a name="showrow"></a>  CDockSite::ShowRow


```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>参数

*pRow*<br/>
[in][in]*bShow* [in] *bAdjustLayout*

### <a name="remarks"></a>备注

##  <a name="swaprows"></a>  CDockSite::SwapRows


```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>参数

*pFirstRow*<br/>
[in][in]*pSecondRow*

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane 类](../../mfc/reference/cbasepane-class.md)
