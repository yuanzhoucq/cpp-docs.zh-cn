---
title: CDockSite Class
ms.date: 10/18/2018
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
ms.openlocfilehash: 471d68ead1bc5a11ace29f572647c4a7f2406b4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753269"
---
# <a name="cdocksite-class"></a>CDockSite Class

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

提供用于排列从 [CPane Class](../../mfc/reference/cpane-class.md) 派生至多组行的窗格的功能。

## <a name="syntax"></a>语法

```
class CDockSite: public CBasePane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|（覆盖[CBasePane：：调整停靠布局](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).）|
|[CDockSite::AdjustLayout](#adjustlayout)|（覆盖[CBasePane：：调整布局](../../mfc/reference/cbasepane-class.md#adjustlayout).）|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|（覆盖[CBasePane：：CalcFixed 布局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).）|
|[CDockSite::CanAcceptPane](#canacceptpane)|（覆盖[CBasePane：：接受窗格](../../mfc/reference/cbasepane-class.md#canacceptpane).）|
|[CDockSite::CreateEx](#createex)|（覆盖[CBasePane：createEx](../../mfc/reference/cbasepane-class.md#createex).）|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|（覆盖[CBasePane：:DockPane](../../mfc/reference/cbasepane-class.md#dockpane).）|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|（覆盖[CBasePane：:DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).）|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite：：获取DockSiteID](#getdocksiteid)||
|[CDock网站：获取Dock网站列表](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|（重写 `CBasePane::IsAccessibilityCompatible`。）|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|（覆盖[CBasePane：可调整大小](../../mfc/reference/cbasepane-class.md#isresizable).|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|返回在停靠站点中给定参数指定的点处停靠的窗格。|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|将窗格停靠到另一个窗格的左侧。|
|[CDockSite：：查找PaneByID](#findpanebyid)|返回由给定 ID 标识的窗格。|
|[CDock网站：获取窗格列表](#getpanelist)|返回停靠在停靠站点的窗格列表。|
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

当您调用`CDockSite`[CFramewndEx：：启用停靠](../../mfc/reference/cframewndex-class.md#enabledocking)时，框架会自动创建对象。 停靠站点窗口位于主框架窗口上的工作区边缘。

您通常不必调用扩展坞站点提供的服务，因为[CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)处理这些服务。

## <a name="example"></a>示例

下面的示例演示如何创建 `CDockSite` 类的对象。

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目标](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>要求

**标题：** afxDockSite.h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a>CDock网站：添加行

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>参数

[在]*pos*<br/>

[在]*nHeight*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockSite：：调整停靠布局

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>备注

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a>CDockSite：：调整布局

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>备注

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a>CDock网站：对齐Dock网站

```cpp
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>参数

[在]*整流比*<br/>

[在]*rectResult*<br/>

[在]*b立即移动*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a>CDock网站：：卡尔卡固定布局

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

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a>CDock网站：：接受窗格

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitecreateex"></a><a name="createex"></a>CDock网站：创建Ex

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

[在]*dwStyleEx*<br/>

[在]*dwStyle*<br/>

[在]*rect*<br/>

[在]*pparentwnd*<br/>

[在]*dwControlBar样式*<br/>

[在]*pContext*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitecreaterow"></a><a name="createrow"></a>CDock网站：创建行

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>参数

[在]*p 父坞栏*<br/>

[在]*n偏移*<br/>

[在]*n 罗高地*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitedockpane"></a><a name="dockpane"></a>CDockSite：:DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

[在]*基方法*<br/>

[在]*lpRect*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a>克多克网站：:D奥克帕内左

将窗格停靠到另一个窗格的左侧。

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>参数

*pBartodock*<br/>
[进出]指向要停靠在*pTargetBar*左侧的窗格的指针。

*p目标栏*<br/>
[进出]指向目标窗格的指针。

### <a name="return-value"></a>返回值

如果窗格已成功停靠，则为 TRUE;如果窗格已成功停靠。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CDockSite：:DoesAllowDynInsert之前

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a>CDockSite：：查找PaneByID

返回具有给定 ID 的窗格。

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]要找到的窗格的命令 ID。

### <a name="return-value"></a>返回值

指向具有指定命令 ID 的窗格的指针，如果未找到窗格，则指向 NULL。

### <a name="remarks"></a>备注

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a>CDock网站：查找罗索引

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>参数

[在]*pRow*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockSite：修复虚拟Rects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>备注

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a>CDockSite：：获取DockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a>CDock网站：获取Dock网站列表

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a>CDock网站：获取窗格列表

返回停靠在停靠站点中的窗格的列表。

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>返回值

对当前停靠栏中停靠的窗格列表的只读引用。

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CDockSite：可访问性兼容

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a>CDockSite：：是德拉格模式

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a>CDockSite：是最后一个

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>参数

[在]*pRow*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a>CDockSite：isrect在DockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

[在]*ptDelta*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a>CDockSite：可调整大小

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksitemovepane"></a><a name="movepane"></a>CDock网站：移动窗格

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

[在]*nFlags*<br/>

[在]*pt偏移*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a>CDockSite：插入器

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>参数

[在]*pos*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a>CDockSite：：在删除行

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>参数

[在]*pos*<br/>

[在]*bByShow*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a>CDockSite：在重新大小行上

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>参数

[在]*prowtoresize*<br/>

[在]*n偏移*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a>CDockSite：：在大小父

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>参数

[在]*重新提供*<br/>

[在]*n侧*<br/>

[在]*b 扩展*<br/>

[在]*n偏移*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a>CDock网站：打开窗口Pos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>参数

[在]*pWndInsert 后*<br/>

[在]*雷克温德*<br/>

[在]*nFlags*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a>CDock网站：在ShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>参数

[在]*pos*<br/>

[在]*b显示*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a>CDockSite：:P从点

返回在停靠站点中给定参数指定的点处停靠的窗格。

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
[在]要检索的窗格的点，位于屏幕坐标中。

### <a name="return-value"></a>返回值

指向位于指定点的窗格的指针，或 NULL 的指针，如果指定点上不存在窗格。

### <a name="remarks"></a>备注

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a>CDockSite：：从点

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

[在]*点*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteremovepane"></a><a name="removepane"></a>CDock网站：删除窗格

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

[在]*基方法*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteremoverow"></a><a name="removerow"></a>CDock 网站：删除行

```cpp
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>参数

[在]*pRow*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a>CDockSite：：替换窗格

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>参数

[在]*pOldBar*<br/>

[在]*pNewBar*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a>CDockSite：：重新定位窗格

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>参数

[在]*rectNewClient区域*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a>CDock网站：调整Dock网站

```cpp
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>参数

[在]*n 新宽度*<br/>

[在]*n 新高度*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a>CDockSite：：调整大小

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>参数

[在]*pRow*<br/>

[在]*n 新尺寸*<br/>

[在]*b 调整布局*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdocksiteshowpane"></a><a name="showpane"></a>CDock网站：：显示窗格

显示窗格。

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[进出]指向要显示或隐藏的窗格的指针。

*b显示*<br/>
[在]TRUE 以指定要显示的窗格;FALSE 以指定要隐藏的窗格。

*bDelay*<br/>
[在]TRUE 指定窗格的布局应延迟到显示窗格之后;否则，请将窗格的布局延迟到否则，FALSE。

*b 激活*<br/>
[在]不使用此参数。

### <a name="return-value"></a>返回值

如果窗格已显示或已成功隐藏，则为 TRUE。 如果指定的窗格不属于此扩展坞站点，则 FALSE。

### <a name="remarks"></a>备注

调用此方法以显示或隐藏停靠的窗格。 通常，您不必直接调用`CDockSite::ShowPane`，因为它由父框架窗口或基窗格调用。

## <a name="cdocksiteshowrow"></a><a name="showrow"></a>CDock网站：显示行

```cpp
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>参数

[在]*pRow*<br/>

[在]*b显示*<br/>

[在]*b 调整布局*<br/>

### <a name="remarks"></a>备注

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a>CDock网站：：交换

```cpp
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>参数

[在]*pFirstRow*<br/>

[在]*p秒罗*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane 类](../../mfc/reference/cbasepane-class.md)
