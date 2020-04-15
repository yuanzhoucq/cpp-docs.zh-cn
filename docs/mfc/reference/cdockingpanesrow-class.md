---
title: CDockingPanesRow 类
ms.date: 10/18/2018
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
ms.openlocfilehash: 8d6a6c4bb9a80dc9170029fd127a052f1bfaddda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375562"
---
# <a name="cdockingpanesrow-class"></a>CDockingPanesRow 类

管理位于停靠站点中同一水平或垂直行（列）的窗格的列表。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CDockingPanesRow : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CDockingPanesRow::CDockingPanesRow`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDockingPanesRow::AddPane](#addpane)||
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||
|[CDocking 窗格行：：排列窗格](#arrangepanes)|根据指定边距和间距参数将窗格排成行。|
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||
|[CDockingPanesRow::Create](#create)||
|[CDocking 窗格行：：展开拉伸窗格](#expandstretchedpanes)||
|[CDocking 窗格行：：展开拉伸窗格 Rect](#expandstretchedpanesrect)||
|[CDockingPanesRow::FixupVirtualRects](#fixupvirtualrects)||
|[CDockingPanerow：：获取可用长度](#getavailablelength)||
|[CDockingPanerow：获取可用空间](#getavailablespace)||
|[CDockingPanerow：：获取客户](#getclientrect)||
|[CDockingPanerow：：获取DockSite](#getdocksite)||
|[CDockingPanerow：获取额外空间](#getextraspace)||
|[CDockingPanerow：从窗格获取群组](#getgroupfrompane)||
|[CDockingPanesRow：GetID](#getid)||
|[CDocking 窗格行：：获取最大窗格大小](#getmaxpanesize)||
|[CDockingPanesRow::GetPaneCount](#getpanecount)||
|[CDockingPanerow：：获取窗格列表](#getpanelist)||
|[CDockingPanesRow：：获取行调](#getrowalignment)||
|[CDockingPanesRow：：获取罗高](#getrowheight)||
|[CDockingPanesRow：：获取罗比](#getrowoffset)||
|[CDockingPanesRow：：获取可见计数](#getvisiblecount)||
|[CDockingPanesRow：：获取窗口重新](#getwindowrect)||
|[CDockingPanesRow::HasPane](#haspane)||
|[CDockingPanesRow::IsEmpty](#isempty)||
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||
|[CDockingPanesRow::IsHorizontal](#ishorizontal)||
|[CDockingPanesRow::IsVisible](#isvisible)||
|[CDockingPanesRow::Move](#move)||
|[CDockingPanesRow::MovePane](#movepane)||
|[CDockingPanesRow::OnResizePane](#onresizepane)||
|[CDockingPanesRow::RedrawAll](#redrawall)||
|[CDockingPanesRow::RemovePane](#removepane)||
|[CDockingPanesRow::ReplacePane](#replacepane)||
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||
|[CDockingPanesRow::Resize](#resize)||
|[CDockingPanesRow::ResizeByPaneDivider](#resizebypanedivider)||
|[CDockingPanesRow::ScreenToClient](#screentoclient)||
|[CDockingPanesRow::SetExtra](#setextra)||
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||
|[CDockingPanesRow::ShowPane](#showpane)||
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||

## <a name="remarks"></a>备注

`CDockingPanesRow` 对象由停靠站点对象在内部创建。

## <a name="example"></a>示例

下面的示例演示如何从 `CMFCAutoHideBar` 对象获取 `CDockingPanesRow` 对象。

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)

## <a name="requirements"></a>要求

**标题：** afxDockingPanesRow.h

## <a name="cdockingpanesrowaddpane"></a><a name="addpane"></a>CDockingPaneRow：：添加窗格

```
virtual void AddPane(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL,
    BOOL bAddLast = FALSE);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

[在]*基方法*<br/>

[在]*lpRect*<br/>

[在]*bAddLast*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowaddpanefromrow"></a><a name="addpanefromrow"></a>CDockingPanerow：：从行添加窗格

```
virtual void AddPaneFromRow(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

[在]*基方法*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowarrangepanes"></a><a name="arrangepanes"></a>CDocking 窗格行：：排列窗格

根据指定的边距和间距参数排列行中的停靠窗格。

```
virtual void ArrangePanes(
    int nMargin,
    int nSpacing);
```

### <a name="parameters"></a>参数

*nMargin*<br/>
[在]从该行的左上角指定第一个窗格的偏移量（以像素为单位）。

*n间距*<br/>
[在]指定窗格之间的间距（以像素为单位）。

### <a name="remarks"></a>备注

调用此方法以排列行中的窗格，这些窗格将停靠在该行中。 调用此方法后，必须调用`CDockingPanesRow::FixupVirtualRects(FALSE, NULL)`。

## <a name="cdockingpanesrowcalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockingPanesRow：：钙固定布局

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

## <a name="cdockingpanesrowcdockingpanesrow"></a><a name="cdockingpanesrow"></a>CDocking 窗格行：：CDockingPanesRow

```
CDockingPanesRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nHeight);
```

### <a name="parameters"></a>参数

[在]*p 父坞栏*<br/>

[在]*n偏移*<br/>

[在]*nHeight*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowcreate"></a><a name="create"></a>CDocking 窗格行：：创建

```
virtual BOOL Create();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowexpandstretchedpanes"></a><a name="expandstretchedpanes"></a>CDocking 窗格行：：展开拉伸窗格

```
void ExpandStretchedPanes();
```

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowexpandstretchedpanesrect"></a><a name="expandstretchedpanesrect"></a>CDocking 窗格行：：展开拉伸窗格 Rect

```
void ExpandStretchedPanesRect();
```

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockingPanesRow：修复虚拟重新

```
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,
    CPane* pBarToExclude = NULL);
```

### <a name="parameters"></a>参数

[在]*b移动返回虚拟rect*<br/>

[在]*pBarto排除*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetavailablelength"></a><a name="getavailablelength"></a>CDockingPanerow：：获取可用长度

```
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;
```

### <a name="parameters"></a>参数

[在]*bUse虚拟重新*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetavailablespace"></a><a name="getavailablespace"></a>CDockingPanerow：获取可用空间

```
virtual void GetAvailableSpace(CRect& rect);
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetclientrect"></a><a name="getclientrect"></a>CDockingPanerow：：获取客户

```
void GetClientRect(CRect& rect) const;
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetdocksite"></a><a name="getdocksite"></a>CDockingPanerow：：获取DockSite

```
CDockSite* GetDockSite() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetextraspace"></a><a name="getextraspace"></a>CDockingPanerow：获取额外空间

```
int GetExtraSpace() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetgroupfrompane"></a><a name="getgroupfrompane"></a>CDockingPanerow：从窗格获取群组

```
void GetGroupFromPane(
    CPane* pBar,
    CObList& lst);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

[在]*奥斯特*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetid"></a><a name="getid"></a>CDockingPanesRow：GetID

```
int GetID() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetmaxpanesize"></a><a name="getmaxpanesize"></a>CDocking 窗格行：：获取最大窗格大小

```
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;
```

### <a name="parameters"></a>参数

[在]*b跳过隐藏栏*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetpanecount"></a><a name="getpanecount"></a>CDockingPanerow：：获取窗格计数

```
int GetPaneCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetpanelist"></a><a name="getpanelist"></a>CDockingPanerow：：获取窗格列表

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetrowalignment"></a><a name="getrowalignment"></a>CDockingPanesRow：：获取行调

```
DWORD GetRowAlignment() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetrowheight"></a><a name="getrowheight"></a>CDockingPanesRow：：获取罗高

```
int GetRowHeight() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetrowoffset"></a><a name="getrowoffset"></a>CDockingPanesRow：：获取罗比

```
int GetRowOffset() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetvisiblecount"></a><a name="getvisiblecount"></a>CDockingPanesRow：：获取可见计数

```
virtual int GetVisibleCount();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowgetwindowrect"></a><a name="getwindowrect"></a>CDockingPanesRow：：获取窗口重新

```
void GetWindowRect(CRect& rect) const;
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowhaspane"></a><a name="haspane"></a>CDockingPanerow：：哈斯帕内

```
BOOL HasPane(CBasePane* pControlBar);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowisempty"></a><a name="isempty"></a>CDockingPanerow：：空

```
virtual BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowisexclusiverow"></a><a name="isexclusiverow"></a>CDockingPanesRow：是排他性的

```
virtual BOOL IsExclusiveRow() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowishorizontal"></a><a name="ishorizontal"></a>CDockingPanerow：：是水平的

```
bool IsHorizontal() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowisvisible"></a><a name="isvisible"></a>CDockingPanesRow：可明显

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowmove"></a><a name="move"></a>CDockingPanesRow：：移动

```
virtual void Move(int nOffset);
```

### <a name="parameters"></a>参数

[在]*n偏移*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowmovepane"></a><a name="movepane"></a>CDockingPaneRow：：移动窗格

```
void MovePane(
    CPane* pControlBar,
    CPoint ptOffset,
    BOOL bSwapControlBars,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    CRect rectTarget,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nOffset,
    bool bForward,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nAbsolutOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

[在]*pt偏移*<br/>

[在]*bSwap控制栏*<br/>

[在]*hdwp*<br/>

[在]*rectTarget*<br/>

[在]*n偏移*<br/>

[在]*b 前进*<br/>

[在]*nAbsolut偏移*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowonresizepane"></a><a name="onresizepane"></a>CDocking 窗格行：：在重新调整窗格上

```
virtual void OnResizePane(CBasePane* pControlBar);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowredrawall"></a><a name="redrawall"></a>CDockingPanerow：：重新绘制所有

```
void RedrawAll();
```

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowremovepane"></a><a name="removepane"></a>CDocking 窗格行：：删除窗格

```
virtual void RemovePane(CPane* pControlBar);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowreplacepane"></a><a name="replacepane"></a>CDocking 窗格行：：替换窗格

```
virtual BOOL ReplacePane(
    CPane* pBarOld,
    CPane* pBarNew);
```

### <a name="parameters"></a>参数

[在]*普巴尔Old*<br/>

[在]*pBar New*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowrepositionpanes"></a><a name="repositionpanes"></a>CDocking 窗格行：：重新定位窗格

```
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,
    UINT nSide = (UINT)-1,
    BOOL bExpand = FALSE,
    int nOffset = 0);
```

### <a name="parameters"></a>参数

[在]*重新家长栏区域*<br/>

[在]*n侧*<br/>

[在]*b 扩展*<br/>

[在]*n偏移*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowresize"></a><a name="resize"></a>CDockingPanerow：：调整大小

```
virtual int Resize(int nOffset);
```

### <a name="parameters"></a>参数

[在]*n偏移*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowresizebypanedivider"></a><a name="resizebypanedivider"></a>CDockingPanerow：：调整大小，由窗格转换器

```
virtual int ResizeByPaneDivider(int /*ignored*/);
```

### <a name="parameters"></a>参数

[在]*忽略*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowscreentoclient"></a><a name="screentoclient"></a>CDockingPanerow：：屏幕到客户端

```
void ScreenToClient(CRect& rect) const;
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowsetextra"></a><a name="setextra"></a>CDockingPanerow：：设置额外

```
void SetExtra(
    int nExtraSpace,
    AFX_ROW_ALIGNMENT rowExtraAlign);
```

### <a name="parameters"></a>参数

[在]*n 额外空间*<br/>

[在]*行额外对齐*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowshowdocksiterow"></a><a name="showdocksiterow"></a>CDockingPanesRow：：显示DockSiteRow

```
virtual void ShowDockSiteRow(
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>参数

[在]*b显示*<br/>

[在]*bDelay*<br/>

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowshowpane"></a><a name="showpane"></a>CDocking 窗格行：：显示窗格

```
virtual BOOL ShowPane(
    CPane* pControlBar,
    BOOL bShow,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>参数

[在]*p控制栏*<br/>

[在]*b显示*<br/>

[在]*bDelay*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockingpanesrowupdatevisiblestate"></a><a name="updatevisiblestate"></a>CDockingPanesRow：：更新可见状态

```
virtual void UpdateVisibleState(BOOL bDelay);
```

### <a name="parameters"></a>参数

[在]*bDelay*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
