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
ms.openlocfilehash: c3600bc5a945c24e91269bc280b4b8e99c54d4c8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750452"
---
# <a name="crecttracker-class"></a>CRectTracker 类

允许以不同方式显示、移动和调整项目。

## <a name="syntax"></a>语法

```
class CRectTracker
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CRect跟踪器：：CRect跟踪器](#crecttracker)|构造 `CRectTracker` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Crect 跟踪器：：调整已调整](#adjustrect)|调整矩形大小时调用。|
|[CRectTracker：:D原](#draw)|渲染矩形。|
|[CRectTracker：:D原始跟踪器Rect](#drawtrackerrect)|绘制对象的边框时`CRectTracker`调用。|
|[CRect 跟踪器：：获取处理掩码](#gethandlemask)|调用以获取`CRectTracker`项的调整大小句柄的掩码。|
|[CRect 跟踪器：：获取 Truerect](#gettruerect)|返回矩形的宽度和高度，包括调整控点的大小。|
|[CRect跟踪器：：命中测试](#hittest)|返回与对象相关的光标的`CRectTracker`当前位置。|
|[CRect 跟踪器：：规范化](#normalizehit)|规范化命中测试代码。|
|[CrectTracker：：打开已更换](#onchangedrect)|在调整大小或移动矩形时调用。|
|[CRect 跟踪器：：设置光标](#setcursor)|设置光标，具体取决于其在矩形上的位置。|
|[CRect 跟踪器：：跟踪](#track)|允许用户操作矩形。|
|[CRectTracker：：轨道橡胶带](#trackrubberband)|允许用户"橡皮筋"的选择。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CRect跟踪：m_nHandleSize](#m_nhandlesize)|确定调整大小控点的大小。|
|[CRectTracker：m_nStyle](#m_nstyle)|跟踪器的当前样式。|
|[CRect跟踪：m_rect](#m_rect)|矩形的当前位置（以像素为单位）。|
|[CRectTracker：：m_sizeMin](#m_sizemin)|确定最小矩形宽度和高度。|

## <a name="remarks"></a>备注

`CRectTracker`没有基类。

尽管该`CRectTracker`类旨在允许用户使用图形界面与 OLE 项进行交互，但其使用并不仅限于启用 OLE 的应用程序。 它可以在需要此类用户界面的任何地方使用。

`CRectTracker`边框可以是实线或虚线。 可以为项目提供阴影边框或覆盖与阴影图案，以指示项目的不同状态。 您可以在项目的外侧或内部边框上放置八个调整大小的控点。 （有关调整大小句柄的说明，请参阅[GetHandleMask](#gethandlemask)。最后，允许您`CRectTracker`在调整大小期间更改项目的方向。

要使用`CRectTracker`，构造`CRectTracker`对象并指定初始化的显示状态。 然后，可以使用此接口向用户提供与对象关联的 OLE 项的当前状态的`CRectTracker`可视反馈。

有关使用`CRectTracker`的详细信息，请参阅文章[跟踪器](../../mfc/trackers.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CRectTracker`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>Crect 跟踪器：：调整已调整

使用调整大小句柄调整跟踪矩形的大小时，由框架调用。

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>参数

*nHandle*<br/>
使用的句柄索引。

*lpRect*<br/>
指向矩形的当前大小的指针。 （矩形的大小由其高度和宽度给出。

### <a name="remarks"></a>备注

此函数的默认行为允许矩形的方向仅在允许反转时更改`Track`和`TrackRubberBand`调用。

覆盖此函数以控制拖动操作期间跟踪矩形的调整。 一种方法是在返回之前调整*lpRect*指定的坐标。

不直接支持的`CRectTracker`特殊功能（如对齐到网格或保持纵横比）可以通过重写此函数来实现。

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRect跟踪器：：CRect跟踪器

创建并初始化一个 `CRectTracker` 对象。

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*lpSrcrect*<br/>
矩形对象的坐标。

*nStyle*<br/>
指定`CRectTracker`对象的样式。 支持以下样式：

- `CRectTracker::solidLine`对矩形边框使用实线。

- `CRectTracker::dottedLine`对矩形边框使用虚线。

- `CRectTracker::hatchedBorder`对矩形边框使用阴影图案。

- `CRectTracker::resizeInside`调整位于矩形内的控点的大小。

- `CRectTracker::resizeOutside`调整位于矩形外部的控点的大小。

- `CRectTracker::hatchInside`阴影图案覆盖整个矩形。

### <a name="remarks"></a>备注

默认构造函数使用`CRectTracker`*lpSrcRect*的值初始化对象，并将其他大小初始化到系统默认值。 如果对象是在没有参数的创建中创建的，则`m_rect``m_nStyle`未初始化 和 数据成员。

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker：:D原

调用此函数以绘制矩形的外线和内部区域。

```cpp
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要绘制的设备上下文的指针。

### <a name="remarks"></a>备注

跟踪器的样式确定绘图的完成方式。 `CRectTracker`有关可用样式的详细信息，请参阅构造函数。

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker：:D原始跟踪器Rect

当跟踪器的位置在`Track`或 成员`TrackRubberBand`函数内发生变化时，由框架调用。

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指针指向`RECT`包含要绘制的矩形的 。

*pwndClipto*<br/>
指向用于裁剪矩形的窗口的指针。

*pDC*<br/>
指向要绘制的设备上下文的指针。

*pwnd*<br/>
指向要在其上进行绘图的窗口。

### <a name="remarks"></a>备注

默认实现对 发出调用`CDC::DrawFocusRect`，该调用绘制一个虚线矩形。

重写此函数以在跟踪操作期间提供不同的反馈。

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRect 跟踪器：：获取处理掩码

框架调用此成员函数以检索矩形调整大小的控点的蒙版。

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>返回值

`CRectTracker`项调整大小的控点的掩码。

### <a name="remarks"></a>备注

调整大小的控点显示在矩形的侧面和角上，并允许用户控制矩形的形状和大小。

矩形有 8 个大小调整控点，编号为 0-7。 每个调整大小的句柄都由掩码中的位表示;该位的值为 2° *n*，*其中 n*是调整大小句柄数。 位 0-3 对应于角调整大小手柄，从左上角顺时针移动。 位 4-7 对应于从顶部顺时针移动的侧调整大小手柄。 下图显示了矩形的调整大小控点及其相应的调整大小句柄数和值：

![调整句柄编号的大小](../../mfc/reference/media/vc35dp1.gif "大小调整控点的数量")

的`GetHandleMask`默认实现返回位的掩码，以便出现调整大小的控点。 如果单个位处于打开，将绘制相应的调整大小控点。

覆盖此成员函数以隐藏或显示指示的调整大小控点。

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRect 跟踪器：：获取 Truerect

调用此函数以检索矩形的坐标。

```cpp
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>参数

*lpTrueRect*<br/>
指向将包含`RECT`对象的设备坐标的结构的`CRectTracker`指针。

### <a name="remarks"></a>备注

矩形的尺寸包括位于外部边框上的任何调整大小的控点的高度和宽度。 返回后 *，lpTrueRect*始终是设备坐标中的规范化矩形。

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRect跟踪器：：命中测试

调用此函数，了解用户是否抓取了调整大小的句柄。

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>参数

*点*<br/>
要测试的点（在设备坐标中）。

### <a name="return-value"></a>返回值

返回的值基于枚举类型`CRectTracker::TrackerHit`，可以具有以下值之一：

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRect跟踪：m_nHandleSize

`CRectTracker`调整大小控点的大小（以像素为单位）。

```
int m_nHandleSize;
```

### <a name="remarks"></a>备注

使用默认系统值初始化。

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRect跟踪：m_rect

矩形在客户端坐标（像素）中的当前位置。

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker：：m_sizeMin

矩形的最小大小。

```
CSize m_sizeMin;
```

### <a name="remarks"></a>备注

默认值`cx`和`cy`都是 根据边框宽度的默认系统值计算的。 此数据成员仅由`AdjustRect`成员函数使用。

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker：m_nStyle

矩形的当前样式。

```
UINT m_nStyle;
```

### <a name="remarks"></a>备注

有关可能样式的列表，请参阅[CRectTracker：：CRectTracker。](#crecttracker)

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRect 跟踪器：：规范化

调用此函数以转换潜在的反转句柄。

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>参数

*nHandle*<br/>
由用户选择的句柄。

### <a name="return-value"></a>返回值

规范化句柄的索引。

### <a name="remarks"></a>备注

当`CRectTracker::Track`允许`CRectTracker::TrackRubberBand`或在允许反转的情况下调用时，矩形可以在 x 轴、y 轴或两者上反转。 发生这种情况时，`HitTest`将返回与矩形有关也反转的控点。 这不适合绘制光标反馈，因为反馈取决于矩形的屏幕位置，而不是要修改的矩形数据结构部分。

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CrectTracker：：打开已更换

每当跟踪器矩形在调用 期间发生更改时，由框架调用`Track`。

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>参数

*rectOld*<br/>
包含`CRectTracker`对象的旧设备坐标。

### <a name="remarks"></a>备注

在调用此功能时，已删除绘制的所有`DrawTrackerRect`反馈。 此函数的默认实现不执行任何操作。

如果要在调整矩形大小后执行任何操作，则重写此函数。

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRect 跟踪器：：设置光标

调用此函数以更改光标形状，而该形状位于对象`CRectTracker`区域上。

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向当前包含光标的窗口。

*nHitTest*<br/>
上一个命中测试的结果，来自WM_SETCURSOR消息。

### <a name="return-value"></a>返回值

如果上次命中超过跟踪器矩形，则非零;否则 0。

### <a name="remarks"></a>备注

从处理WM_SETCURSOR消息的窗口函数内部调用此函数（通常`OnSetCursor`为 ）。

## <a name="crecttrackertrack"></a><a name="track"></a>CRect 跟踪器：：跟踪

调用此函数以显示用于调整矩形大小的用户界面。

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
包含矩形的窗口对象。

*点*<br/>
当前鼠标位置相对于工作区的设备坐标。

*布劳弗*<br/>
如果为 TRUE，矩形可以沿 x 轴或 y 轴反转;如果为 TRUE，则矩形可以沿 x 轴或 y 轴反转。否则 FALSE。

*pwndClipto*<br/>
绘图操作将剪切到的窗口。 如果 NULL，*则 pWnd*用作裁剪矩形。

### <a name="return-value"></a>返回值

如果按下 ESC 键，跟踪过程将停止，存储在跟踪器中的矩形不会更改，并且返回 0。 如果提交更改，通过移动鼠标并释放鼠标左键，新位置和/或大小将记录在跟踪器的矩形中，并且返回非零。

### <a name="remarks"></a>备注

这通常是从处理消息的应用程序的函数内部调用的`WM_LBUTTONDOWN`（通常`OnLButtonDown`为 ）。

此功能将捕获鼠标，直到用户释放鼠标左键、按下 ESC 键或按下鼠标右键。 当用户移动鼠标光标时，反馈将通过调用`DrawTrackerRect`和`OnChangedRect`更新。

如果*bAllowInvert*为 TRUE，则可以在 x 轴或 y 轴上反转跟踪矩形。

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker：：轨道橡胶带

调用此函数以执行橡皮筋选择。

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
包含矩形的窗口对象。

*点*<br/>
当前鼠标位置相对于工作区的设备坐标。

*布劳弗*<br/>
如果为 TRUE，矩形可以沿 x 轴或 y 轴反转;如果为 TRUE，则矩形可以沿 x 轴或 y 轴反转。否则 FALSE。

### <a name="return-value"></a>返回值

如果鼠标已移动且矩形不为空，则非零;否则 0。

### <a name="remarks"></a>备注

它通常从处理WM_LBUTTONDOWN消息的应用程序函数内部调用（通常`OnLButtonDown`为 ）。

此功能将捕获鼠标，直到用户释放鼠标左键、按下 ESC 键或按下鼠标右键。 当用户移动鼠标光标时，反馈将通过调用`DrawTrackerRect`和`OnChangedRect`更新。

跟踪使用右下角手柄的橡皮带类型选择进行。 如果允许反转，则可以通过向上、向左或向下和向右拖动来调整矩形的大小。

## <a name="see-also"></a>请参阅

[MFC 样品跟踪器](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar 类](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect 类](../../atl-mfc-shared/reference/crect-class.md)
