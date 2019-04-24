---
title: CRectTracker 类
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 9c54cdfecfa6c4ff0eef7e16003ab2097553953d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775681"
---
# <a name="crecttracker-class"></a>CRectTracker 类

允许显示、 移动和不同方式调整大小选项。

## <a name="syntax"></a>语法

```
class CRectTracker
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|构造 `CRectTracker` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|当调整大小矩形时调用。|
|[CRectTracker::Draw](#draw)|呈现矩形。|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|当绘制的边框时调用`CRectTracker`对象。|
|[CRectTracker::GetHandleMask](#gethandlemask)|调用以获取的掩码`CRectTracker`项的调整大小图柄。|
|[CRectTracker::GetTrueRect](#gettruerect)|返回矩形，包括重设大小句柄的宽度和高度。|
|[CRectTracker::HitTest](#hittest)|返回与光标的当前位置`CRectTracker`对象。|
|[CRectTracker::NormalizeHit](#normalizehit)|规范化的命中测试代码。|
|[CRectTracker::OnChangedRect](#onchangedrect)|当已调整大小或移动矩形时调用。|
|[CRectTracker::SetCursor](#setcursor)|设置光标，具体取决于它对矩形的位置。|
|[CRectTracker::Track](#track)|允许用户用来处理该矩形。|
|[CRectTracker::TrackRubberBand](#trackrubberband)|允许用户向"橡皮筋"选择。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|确定大小的调整大小图柄。|
|[CRectTracker::m_nStyle](#m_nstyle)|跟踪器的当前 style(s)。|
|[CRectTracker::m_rect](#m_rect)|（以像素为单位） 的矩形的当前位置。|
|[CRectTracker::m_sizeMin](#m_sizemin)|确定最小矩形宽度和高度。|

## <a name="remarks"></a>备注

`CRectTracker` 没有基类。

尽管`CRectTracker`类旨在允许用户与 OLE 项通过图形界面进行交互，其用途并不局限于 OLE 启用应用程序。 可以使用此类用户界面的所需的任意位置。

`CRectTracker` 可以是实线边框或点线。 可以给出阴影的边框或重叠结构与阴影模式以指示不同状态的项的项。 可以将八个调整大小图柄放在外部或内部项的边框。 (重设大小句柄的说明，请参阅[GetHandleMask](#gethandlemask)。)最后，`CRectTracker`允许您更改期间调整大小的项的方向。

若要使用`CRectTracker`，构造`CRectTracker`对象，并指定哪些显示状态进行初始化。 然后可以使用此接口以提供有关与关联的 OLE 项的当前状态的用户视觉反馈`CRectTracker`对象。

有关使用的详细信息`CRectTracker`，请参阅文章[跟踪器](../../mfc/trackers.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CRectTracker`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="adjustrect"></a>  CRectTracker::AdjustRect

跟踪矩形使用重设大小句柄重设大小时，由框架调用。

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>参数

*nHandle*<br/>
使用句柄的索引。

*lpRect*<br/>
指向当前矩形的大小。 （一个矩形的大小由给定其高度和宽度。）

### <a name="remarks"></a>备注

此函数的默认行为允许矩形的方向更改时，才`Track`和`TrackRubberBand`使用反转允许调用。

重写此函数可控制在拖动操作期间跟踪矩形的调整。 一种方法是调整指定的坐标*lpRect*在返回之前。

不直接支持的特殊功能`CRectTracker`，如对齐网格或保持纵横比，可以实现通过重写此函数。

##  <a name="crecttracker"></a>  CRectTracker::CRectTracker

创建并初始化`CRectTracker`对象。

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*lpSrcRect*<br/>
Rectangle 对象的坐标。

*nStyle*<br/>
指定的样式`CRectTracker`对象。 支持以下样式：

- `CRectTracker::solidLine` 矩形边框所使用一条实线。

- `CRectTracker::dottedLine` 矩形边框所使用点线。

- `CRectTracker::hatchedBorder` 矩形边框所使用的阴影的模式。

- `CRectTracker::resizeInside` 重设大小句柄位于矩形内。

- `CRectTracker::resizeOutside` 重设大小句柄位于矩形外。

- `CRectTracker::hatchInside` 影线模式涵盖整个矩形。

### <a name="remarks"></a>备注

默认构造函数初始化`CRectTracker`对象的值从*lpSrcRect*并初始化其他大小为系统默认值。 如果不带任何参数，创建对象`m_rect`和`m_nStyle`数据成员均未初始化。

##  <a name="draw"></a>  CRectTracker::Draw

调用此函数可绘制矩形的外部直线和内部区域。

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>参数

*pDC*<br/>
在其上绘制的设备上下文的指针。

### <a name="remarks"></a>备注

跟踪器的样式确定如何完成绘图。 请参阅的构造函数`CRectTracker`的可用样式的详细信息。

##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect

每当跟踪器的位置发生更改时由框架调用而内部`Track`或`TrackRubberBand`成员函数。

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`，其中包含要绘制的矩形。

*pWndClipTo*<br/>
指向要在剪切矩形中使用的窗口。

*pDC*<br/>
在其上绘制的设备上下文的指针。

*pWnd*<br/>
指向窗口会在其绘制的指针。

### <a name="remarks"></a>备注

默认实现将调用`CDC::DrawFocusRect`，它可绘制虚的框。

重写此函数可在跟踪操作过程中提供其他反馈。

##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask

框架调用此成员函数以检索掩码的矩形的大小调整句柄。

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>返回值

掩码`CRectTracker`项的调整大小图柄。

### <a name="remarks"></a>备注

调整大小图柄出现边和矩形的角变，而允许用户控制的形状和矩形的大小。

矩形具有 8 编号为 0 到 7 的调整大小图柄。 每个重设大小句柄由表示位掩码; 中该位的值为 2 ^ *n*，其中*n*是重设大小句柄数。 0-3 位对应于角调整大小图柄，从左上方移动顺时针旋转。 Bits 4-7 对应于在端调整大小图柄沿顺时针方向移动顶部开始。 下图显示矩形的调整手柄和及其相应的调整大小控点的数量和值：

![大小调整句柄的数量](../../mfc/reference/media/vc35dp1.gif "调整大小控点的数量")

默认实现`GetHandleMask`返回的位掩码，以便显示调整大小控点。 如果单个位是打开的将绘制相应的调整大小图柄。

重写此成员函数以隐藏或显示所指示的重设大小句柄。

##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect

调用此函数可检索的矩形的坐标。

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>参数

*lpTrueRect*<br/>
指向`RECT`结构，它将包含设备坐标`CRectTracker`对象。

### <a name="remarks"></a>备注

矩形的尺寸包括的高度和宽度的外边框上任何调整大小图柄。 在返回时， *lpTrueRect*始终是以设备坐标表示规范化的矩形。

##  <a name="hittest"></a>  CRectTracker::HitTest

调用此函数可了解用户是否已获取重设大小句柄。

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>参数

*point*<br/>
以设备坐标，若要测试的点。

### <a name="return-value"></a>返回值

基于枚举的类型，则返回该值`CRectTracker::TrackerHit`，可以具有以下值之一：

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6

- `CRectTracker::hitLeft` 7

- `CRectTracker::hitMiddle` 8

##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize

大小，以像素为单位的`CRectTracker`重设大小句柄。

```
int m_nHandleSize;
```

### <a name="remarks"></a>备注

使用默认系统值进行初始化。

##  <a name="m_rect"></a>  CRectTracker::m_rect

在工作区坐标 （像素） 的矩形的当前位置。

```
CRect m_rect;
```

##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin

矩形的最小大小。

```
CSize m_sizeMin;
```

### <a name="remarks"></a>备注

这两个默认值，`cx`和`cy`，边框宽度的默认系统值进行计算。 此数据成员仅供`AdjustRect`成员函数。

##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle

矩形的当前样式。

```
UINT m_nStyle;
```

### <a name="remarks"></a>备注

请参阅[CRectTracker::CRectTracker](#crecttracker)有关可能的样式的列表。

##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit

调用此函数将转换可能倒排的句柄。

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>参数

*nHandle*<br/>
用户选择的句柄。

### <a name="return-value"></a>返回值

规范化的句柄的索引。

### <a name="remarks"></a>备注

当`CRectTracker::Track`或`CRectTracker::TrackRubberBand`称为使用反转允许，很可能要反转 x 轴、 y 轴或两者的矩形。 在此情况下，`HitTest`将返回还反转相对于矩形的句柄。 这是不适合于绘制光标反馈，因为反馈取决于矩形，不会被修改的矩形数据结构的部分的屏幕位置。

##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect

每当跟踪器矩形的调用过程中发生更改时由框架调用`Track`。

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>参数

*rectOld*<br/>
包含的旧设备坐标`CRectTracker`对象。

### <a name="remarks"></a>备注

在时调用此函数，使用绘制的所有反馈`DrawTrackerRect`已删除。 此函数的默认实现不执行任何操作。

如果想要执行任何操作，该矩形具有调整大小后，重写此函数。

##  <a name="setcursor"></a>  CRectTracker::SetCursor

调用此函数可更改光标形状触`CRectTracker`对象的区域。

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向当前包含光标的窗口。

*nHitTest*<br/>
WM_SETCURSOR 消息从上一个命中测试的结果。

### <a name="return-value"></a>返回值

如果上一个命中是通过跟踪器矩形; 非零值否则为 0。

### <a name="remarks"></a>备注

内部调用此函数从处理 WM_SETCURSOR 消息在窗口的函数 (通常`OnSetCursor`)。

##  <a name="track"></a>  CRectTracker::Track

调用此函数可显示用户界面，以便调整矩形大小。

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
包含矩形的窗口对象。

*point*<br/>
设备的当前鼠标位置相对于客户端区域的坐标。

*bAllowInvert*<br/>
如果为 TRUE，该矩形可以反转沿 x 轴或 y 轴;否则为 FALSE。

*pWndClipTo*<br/>
绘制操作将剪辑到窗口。 如果为 NULL， *pWnd*用作的剪辑矩形。

### <a name="return-value"></a>返回值

如果按下 ESC 键时，跟踪进程将暂停，不更改跟踪器中存储的矩形，并返回 0。 则提交更改，通过将鼠标并释放鼠标左键，新的位置和/或大小记录的跟踪器的矩形中，并返回非零值。

### <a name="remarks"></a>备注

这通常称为从处理应用程序在函数内`WM_LBUTTONDOWN`消息 (通常`OnLButtonDown`)。

此函数将捕获鼠标，直到用户释放鼠标左键、 按 ESC 键，或按下鼠标右键。 当用户移动鼠标光标时，通过调用更新反馈`DrawTrackerRect`和`OnChangedRect`。

如果*bAllowInvert*为 TRUE 时，跟踪矩形可以反转 x 轴或 y 轴上。

##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand

调用此函数可执行橡皮筋选择。

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
包含矩形的窗口对象。

*point*<br/>
设备的当前鼠标位置相对于客户端区域的坐标。

*bAllowInvert*<br/>
如果为 TRUE，该矩形可以反转沿 x 轴或 y 轴;否则为 FALSE。

### <a name="return-value"></a>返回值

如果鼠标移动并且该矩形不是空，则为非零值否则为 0。

### <a name="remarks"></a>备注

它通常从内部处理 WM_LBUTTONDOWN 消息应用程序的函数调用 (通常`OnLButtonDown`)。

此函数将捕获鼠标，直到用户释放鼠标左键、 按 ESC 键，或按下鼠标右键。 当用户移动鼠标光标时，通过调用更新反馈`DrawTrackerRect`和`OnChangedRect`。

通过从右下角的图柄橡胶带类型选择执行跟踪。 如果允许反转，则可以通过拖动是向上和向左或向下和向右大小调整矩形。

## <a name="see-also"></a>请参阅

[MFC 示例跟踪器](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar 类](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)
