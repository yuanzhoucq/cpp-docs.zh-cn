---
title: CScrollView 类
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: 5d0eb163fae2aa5fc63470e1c499311ab1a402a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754419"
---
# <a name="cscrollview-class"></a>CScrollView 类

具有滚动功能的[CView。](../../mfc/reference/cview-class.md)

## <a name="syntax"></a>语法

```
class CScrollView : public CView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CScroll查看：CScroll查看](#cscrollview)|构造 `CScrollView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CScroll查看：：检查滚动条](#checkscrollbars)|指示滚动视图是否具有水平和垂直滚动条。|
|[CScroll 查看：：填充外部重新](#filloutsiderect)|填充滚动区域外的视图区域。|
|[CScroll查看：获取设备滚动位置](#getdevicescrollposition)|获取设备单位的当前滚动位置。|
|[CScroll 查看：：获取设备滚动大小](#getdevicescrollsizes)|获取可滚动视图的当前映射模式、总大小以及行和页面大小。 大小以设备单位为单位。|
|[CScroll查看：获取滚动位置](#getscrollposition)|获取逻辑单位的当前滚动位置。|
|[CScroll 查看：获取总计大小](#gettotalsize)|获取逻辑单位滚动视图的总大小。|
|[CScrollView：调整父级](#resizeparenttofit)|使视图的大小决定其帧的大小。|
|[CScroll查看：：滚动位置](#scrolltoposition)|将视图滚动到给定点，以逻辑单位指定。|
|[CScroll查看：：设置比例调整尺寸](#setscaletofitsize)|将滚动视图置于缩放到拟合模式。|
|[CScroll查看：：设置滚动大小](#setscrollsizes)|设置滚动视图的映射模式、总大小以及水平和垂直滚动量。|

## <a name="remarks"></a>备注

您可以通过重写消息映射的[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和`CView`[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数来处理从派生的任何类中的标准滚动。 但是`CScrollView`，将以下功能添加到其`CView`功能中：

- 它管理窗口和视口大小以及映射模式。

- 它会自动滚动以响应滚动条消息。

- 它会自动滚动以响应来自键盘、非滚动鼠标或 IntelliMouse 滚轮的消息。

要自动滚动以响应来自键盘的消息，请添加WM_KEYDOWN消息，并测试VK_DOWN、VK_PREV和调用[SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos)。

您可以通过重写消息映射的[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[On 注册鼠标滚轮](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成员功能来处理鼠标滚轮。 由于它们的作用`CScrollView`，这些成员函数支持[WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel)的建议行为，即车轮旋转消息。

要利用自动滚动，请从`CScrollView`派生视图类，而不是从`CView`派生。 首次创建视图时，如果要根据文档的大小计算可滚动视图的大小，请从`SetScrollSizes`[CView：：上初始更新](../../mfc/reference/cview-class.md#oninitialupdate)或[CView：：onUpdate](../../mfc/reference/cview-class.md#onupdate)的重写调用成员函数。 （您必须编写自己的代码来查询文档的大小。 例如，请参阅[涂鸦示例](../../overview/visual-cpp-samples.md)。

对成员函数的`SetScrollSizes`调用设置视图的映射模式、滚动视图的总尺寸以及水平和垂直滚动的量。 所有大小均以逻辑单位为单位。 视图的逻辑大小通常根据存储在文档中的数据计算，但在某些情况下，您可能需要指定固定大小。 有关这两种方法的示例，请参阅[CScrollView：：设置ScrollSizes](#setscrollsizes)。

指定以逻辑单位水平和垂直滚动的金额。 默认情况下，如果用户单击滚动框外的滚动条轴，则`CScrollView`滚动"页面"。 如果用户单击滚动条两端的滚动箭头，`CScrollView`则滚动"行"。 默认情况下，页面是视图总大小的 1/10;如果页面大小，则为 1/10。一行是页面大小的 1/10。 通过在成员函数中传递自定义大小来`SetScrollSizes`覆盖这些默认值。 例如，您可以将水平大小设置为总大小宽度的一部分，将垂直大小设置为当前字体中行的高度。

可以自动将视图缩放`CScrollView`到当前窗口大小，而不是滚动。 在此模式下，视图没有滚动条，并且逻辑视图将拉伸或收缩，以完全适合窗口的工作区。 要使用此"缩放到拟合"功能，请致电[CScrollView：：设置ScaletoFitSize](#setscaletofitsize)。 （呼叫任`SetScaleToFitSize`一`SetScrollSizes`或 ，但不能同时呼叫两者。

在`OnDraw`调用派生视图类的成员函数之前，`CScrollView`自动调整它传递给`CPaintDC``OnDraw`的设备上下文对象的视点源。

要调整滚动窗口的视口原点，`CScrollView`请覆盖[CView：：onPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 此调整对于`CPaintDC`传递给`CScrollView``OnDraw`的设备上下文是自动的，但您必须针对您使用`CScrollView::OnPrepareDC`的任何其他设备上下文（如`CClientDC`。 您可以重写`CScrollView::OnPrepareDC`以设置笔、背景色和其他绘图属性，但调用基类执行缩放。

滚动条可以相对于视图出现在三个位置，如以下情况所示：

- 可以使用 WS_HSCROLL 和 WS_VSCROLL[Windows 样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)为视图设置标准窗口样式滚动条。

- 滚动条控件也可以添加到包含视图的帧中，在这种情况下，框架会将WM_HSCROLL转发，并将消息 WM_VSCROLL从框架窗口转发到当前活动视图。

- 框架还将滚动消息从`CSplitterWnd`拆分器控件转发到当前活动的拆分器窗格（视图）。 当放置在带有共享滚动条的[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)中`CScrollView`时，对象将使用共享滚动条，而不是创建自己的滚动条。

有关使用`CScrollView`的详细信息，请参阅[MFC 中可用的文档/视图体系结构](../../mfc/document-view-architecture.md)和[派生视图类](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScroll查看：：检查滚动条

调用此成员函数以确定滚动视图是否具有水平和垂直条。

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>参数

*b哈斯霍兹酒吧*<br/>
指示应用程序具有水平滚动条。

*bHasvertbar*<br/>
指示应用程序具有垂直滚动条。

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScroll查看：CScroll查看

构造 `CScrollView` 对象。

```
CScrollView();
```

### <a name="remarks"></a>备注

您必须在滚动`SetScrollSizes`视图可用`SetScaleToFitSize`之前调用。

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScroll 查看：：填充外部重新

调用`FillOutsideRect`以填充显示在滚动区域外部的视图区域。

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>参数

*pDC*<br/>
要完成填充的设备上下文。

*pBrush*<br/>
要填充区域的刷子。

### <a name="remarks"></a>备注

在`FillOutsideRect`滚动视图的`OnEraseBkgnd`处理程序函数中使用，以防止过度重新绘制背景。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScroll查看：获取设备滚动位置

当您`GetDeviceScrollPosition`需要滚动条中滚动框的当前水平和垂直位置时，请呼叫。

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>返回值

滚动框作为`CPoint`对象的水平和垂直位置（以设备单位为单位）。

### <a name="remarks"></a>备注

此坐标对对应于文档中已滚动视图左上角的位置。 这对于抵消鼠标设备位置以滚动查看设备位置非常有用。

`GetDeviceScrollPosition`返回以设备单位为单位的值。 如果需要逻辑单位，请使用`GetScrollPosition`。

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScroll 查看：：获取设备滚动大小

`GetDeviceScrollSizes`获取可滚动视图的当前映射模式、总大小以及行和页面大小。

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>参数

*nMapMode*<br/>
返回此视图的当前映射模式。 有关可能值的列表，请参见 `SetScrollSizes`。

*大小 总计*<br/>
以设备单位返回滚动视图的当前总大小。

*大小页*<br/>
返回当前水平和垂直量，以响应滚动条轴中的鼠标单击，在每个方向上滚动。 成员`cx`包含水平量。 成员`cy`包含垂直量。

*大小线*<br/>
返回当前水平和垂直量，以响应滚动箭头中的鼠标单击，在每个方向上滚动。 成员`cx`包含水平量。 成员`cy`包含垂直量。

### <a name="remarks"></a>备注

大小以设备单位为单位。 很少调用此成员函数。

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScroll查看：获取滚动位置

当您`GetScrollPosition`需要滚动条中滚动框的当前水平和垂直位置时，请呼叫。

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>返回值

滚动框作为`CPoint`对象的水平和垂直位置（以逻辑单位表示）。

### <a name="remarks"></a>备注

此坐标对对应于文档中已滚动视图左上角的位置。

`GetScrollPosition`返回逻辑单位中的值。 如果需要设备单元，请使用`GetDeviceScrollPosition`。

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScroll 查看：获取总计大小

调用`GetTotalSize`以检索滚动视图的当前水平和垂直大小。

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>返回值

以逻辑单位表示滚动视图的总大小。 水平大小位于返回值`cx`的成员中。 `CSize` 垂直大小位于成员中`cy`。

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView：调整父级

调用`ResizeParentToFit`以让视图的大小决定其框架窗口的大小。

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>参数

*b收缩仅*<br/>
要执行的调整大小。 默认值 TRUE 会收缩帧窗口（如果适用）。 对于大型视图或小框架窗口，仍会出现滚动条。 FALSE 的值会导致视图始终精确调整帧窗口的大小。 这可能有点危险，因为框架窗口可能变得太大，无法容纳多个文档界面 （MDI） 框架窗口或屏幕。

### <a name="remarks"></a>备注

这仅适用于 MDI 子框架窗口中的视图。 `ResizeParentToFit`在`OnInitialUpdate`派生`CScrollView`类的处理程序函数中使用。 有关此成员函数的示例，请参阅[CScrollView：：设置ScrollSizes](#setscrollsizes)。

`ResizeParentToFit`假定视图窗口的大小已设置。 如果在调用时`ResizeParentToFit`尚未设置视图窗口大小，您将获得断言。 为确保不会发生这种情况，请先调用`ResizeParentToFit`：

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScroll查看：：滚动位置

调用`ScrollToPosition`以滚动到视图中的给定点。

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
以逻辑单位滚动到的点。 成员`x`必须为正值（大于或等于 0，最多为视图的总大小）。 当映射模式MM_TEXT时，`y`成员也是如此。 在`y`映射模式（MM_TEXT 之外，成员为负值。

### <a name="remarks"></a>备注

视图将被滚动，以便此点位于窗口的左上角。 如果视图已缩放为适合，则不得调用此成员函数。

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScroll查看：：设置比例调整尺寸

如果要`SetScaleToFitSize`自动将视口大小缩放到当前窗口大小，请进行调用。

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>参数

*大小 总计*<br/>
要缩放视图的水平和垂直大小。 滚动视图的大小以逻辑单位度量。 水平大小包含在成员中`cx`。 垂直大小包含在成员中`cy`。 `cx`和`cy`必须大于或等于 0。

### <a name="remarks"></a>备注

使用滚动条时，逻辑视图的一部分可能随时可见。 但是，使用"缩放到拟合"功能，视图没有滚动条，并且逻辑视图会拉伸或收缩，以完全适合窗口的工作区。 调整窗口大小时，视图将根据窗口的大小以新比例绘制其数据。

通常，您将在覆盖视图`SetScaleToFitSize``OnInitialUpdate`的成员函数时将调用置于该函数的覆盖位置。 如果不希望自动缩放，`SetScrollSizes`请改为调用成员函数。

`SetScaleToFitSize`可用于实现"缩放到适合"操作。 用于`SetScrollSizes`重新初始化滚动。

`SetScaleToFitSize`假定视图窗口的大小已设置。 如果在调用时`SetScaleToFitSize`尚未设置视图窗口大小，您将获得断言。 为确保不会发生这种情况，请先调用`SetScaleToFitSize`：

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScroll查看：：设置滚动大小

当`SetScrollSizes`视图即将更新时调用。

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>参数

*nMapMode*<br/>
要为此视图设置的映射模式。 可能的值包括：

|映射模式|逻辑单元|正 y 轴 延伸...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 像素|向下|
|MM_HIMETRIC|0.01 毫米|向上|
|MM_TWIPS|1/1440 in|向上|
|MM_HIENGLISH|0.001 in|向上|
|MM_LOMETRIC|0.1 毫米|向上|
|MM_LOENGLISH|0.01 in|向上|

所有这些模式都由 Windows 定义。 MM_ISOTROPIC和MM_ANISOTROPIC两种标准映射模式不用于`CScrollView`。 类库提供成员函数`SetScaleToFitSize`，用于将视图缩放到窗口大小。 上表第三列描述了坐标方向。

*大小 总计*<br/>
滚动视图的总大小。 成员`cx`包含水平范围。 成员`cy`包含垂直范围。 大小以逻辑单位表示。 `cx`和`cy`必须大于或等于 0。

*大小页*<br/>
水平和垂直量要在每个方向滚动，以响应滚动条轴中的鼠标单击。 成员`cx`包含水平量。 成员`cy`包含垂直量。

*大小线*<br/>
水平和垂直量要在每个方向滚动，以响应滚动箭头中的鼠标单击。 成员`cx`包含水平量。 成员`cy`包含垂直量。

### <a name="remarks"></a>备注

在成员函数的`OnUpdate`重写中调用它，以在最初显示文档或更改大小时调整滚动特征。

您通常会通过调用文档成员函数（可能称为`GetMyDocSize`，与派生文档类一起提供）从视图的关联文档中获取大小信息。 以下代码显示了此方法：

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

或者，有时您可能需要设置固定大小，如以下代码：

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

您必须将映射模式设置为除MM_ISOTROPIC或MM_ANISOTROPIC以外的任何 Windows 映射模式。 如果要使用无约束映射模式，`SetScaleToFitSize`请调用成员函数而不是`SetScrollSizes`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)
