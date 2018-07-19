---
title: CScrollView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43ad1d1d047b9e44da27d1c9eb24dde39fd429ef
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849911"
---
# <a name="cscrollview-class"></a>CScrollView 类
一个[CView](../../mfc/reference/cview-class.md)带滚动功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CScrollView : public CView  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CScrollView::CScrollView](#cscrollview)|构造 `CScrollView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CScrollView::CheckScrollBars](#checkscrollbars)|指示滚动视图是否具有水平和垂直滚动条。|  
|[CScrollView::FillOutsideRect](#filloutsiderect)|填充的视图滚动区之外的区域。|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|获取当前的滚动位置以设备为单位。|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|获取当前的映射模式、 的总大小和可滚动视图的行和页大小。 大小为设备单位。|  
|[CScrollView::GetScrollPosition](#getscrollposition)|获取逻辑单元中的当前滚动位置。|  
|[CScrollView::GetTotalSize](#gettotalsize)|获取逻辑单元中滚动视图的总大小。|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|导致要决定其帧的大小的视图的大小。|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|滚动到给定的点，请指定逻辑单元中的视图。|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|将滚动视图放入规模调整模式。|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|设置滚动视图的映射模式、 总大小和水平和垂直滚动量。|  
  
## <a name="remarks"></a>备注  
 您可以处理派生自任何类中滚动自己的标准`CView`通过重写消息映射[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)并[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数。 但是`CScrollView`添加到了以下功能及其`CView`功能：  
  
-   它管理窗口和视区大小和映射模式。  
  
-   它会自动滚动以响应滚动条消息。  
  
-   它会自动滚动以响应消息从键盘、 非滚动鼠标或智能鼠标滚轮。  
  
 若要在响应消息从键盘自动滚动，添加对 WM_KEYDOWN 消息，并测试 VK_DOWN、 VK_PREV 和调用[SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 您可以处理鼠标滚轮滚动自己通过重写消息映射[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)并[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成员函数。 因为它们是用于`CScrollView`，这些成员函数支持的建议的行为[对 wm_mousewheel 进行](http://msdn.microsoft.com/library/windows/desktop/ms645617)，鼠标轮旋转消息。  
  
 若要充分利用自动滚动，派生视图类从`CScrollView`而不是从`CView`。 该视图是首次创建时，如果你想要计算的基于大小的文档，调用的可滚动视图大小`SetScrollSizes`通过重写的成员函数[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)。 （您必须编写您自己的代码来查询文档的大小。 有关示例，请参阅[Scribble 示例](../../visual-cpp-samples.md)。)  
  
 对调用`SetScrollSizes`成员函数将设置视图的映射模式下，滚动视图和水平或垂直地滚动的金额的总的维度。 所有尺寸都都以逻辑单位。 该视图的逻辑大小通常计算从数据存储在文档中，但在某些情况下，可能想要指定固定的大小。 有关这两种方法的示例，请参阅[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 指定水平或垂直地滚动以逻辑单位的数量。 默认情况下，如果用户单击的滚动条轴滚动框的外部`CScrollView`滚动"page"。 如果用户单击任意一端的滚动条的滚动箭头`CScrollView`滚动"行"。 默认情况下，一个页面是视图; 的总大小的 1/10线路是页面大小的 1/10。 通过传递自定义大小中的重写这些默认值`SetScrollSizes`成员函数。 例如，您可能设置的水平大小为总大小和行的高度的垂直大小的宽度的某些部分中的当前字体。  
  
 而不是滚动，`CScrollView`可以自动缩放到当前窗口大小的视图。 在此模式下，此视图具有任何滚动条和拉伸或收缩以完全适合窗口的工作区的逻辑视图。 若要使用此规模调整功能，请调用[CScrollView::SetScaleToFitSize](#setscaletofitsize)。 (调用`SetScaleToFitSize`或`SetScrollSizes`，但不可同时使用两者。)  
  
 之前`OnDraw`称为派生的视图类的成员函数，`CScrollView`自动进行调整的视区原点`CPaintDC`设备上下文对象，它将传递给`OnDraw`。  
  
 若要调整滚动的窗口中，视区原点`CScrollView`重写[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 将自动进行此调整`CPaintDC`设备上下文的`CScrollView`将传递给`OnDraw`，但必须调用`CScrollView::OnPrepareDC`自己用于任何其他设备上下文的使用，如`CClientDC`。 您可以重写`CScrollView::OnPrepareDC`设置笔、 背景色和其他绘制特性，但调用基类来进行缩放。  
  
 在以下情况下所示，可以在以下三个位置相对于视图中显示滚动条：  
  
-   标准的窗口样式滚动条可以设置为视图使用 WS_HSCROLL 和 WS_VSCROLL[Windows 样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
-   滚动条控件还可以添加到包含该视图的框架，这种情况下该框架将转发 WM_HSCROLL 和 WM_VSCROLL 消息从框架窗口的当前活动视图。  
  
-   该框架还将转发滚动消息从`CSplitterWnd`到当前处于活动状态的拆分器窗格 （视图） 的拆分器控件。 中放入时[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)带共享的滚动条，`CScrollView`对象将使用共享的而不是无需创建其自身。  
  
 有关使用的详细信息`CScrollView`，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)并[派生视图类 MFC 中可用](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars  
 调用此成员函数来确定滚动视图是否具有水平和垂直条。  
  
```  
void CheckScrollBars(
    BOOL& bHasHorzBar,  
    BOOL& bHasVertBar) const;  
```  
  
### <a name="parameters"></a>参数  
 *bHasHorzBar*  
 指示应用程序具有水平滚动条。  
  
 *bHasVertBar*  
 指示应用程序具有垂直滚动条。  
  
##  <a name="cscrollview"></a>  CScrollView::CScrollView  
 构造 `CScrollView` 对象。  
  
```  
CScrollView();
```  
  
### <a name="remarks"></a>备注  
 您必须调用`SetScrollSizes`或`SetScaleToFitSize`之前滚动视图是可用。  
  
##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect  
 调用`FillOutsideRect`以填充视图滚动区之外显示的区域。  
  
```  
void FillOutsideRect(
    CDC* pDC,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 设备上下文是用来进行填充。  
  
 *pBrush*  
 画笔的区域填充是。  
  
### <a name="remarks"></a>备注  
 使用`FillOutsideRect`中滚动视图的`OnEraseBkgnd`处理程序函数，以防止过多的背景重新绘制。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition  
 调用`GetDeviceScrollPosition`时所需的当前水平和垂直位置的滚动框在滚动条。  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 水平和垂直位置 （以设备为单位） 的滚动框作为`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 此坐标对对应于视图的左上角已滚动到文档中的位置。 这可用于抵销滚动查看设备职位的鼠标设备位置。  
  
 `GetDeviceScrollPosition` 返回以设备为单位的值。 如果想要的逻辑单元，使用`GetScrollPosition`相反。  
  
##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes  
 `GetDeviceScrollSizes` 获取当前的映射模式、 的总大小和可滚动视图的行和页大小。  
  
```  
void GetDeviceScrollSizes(
    int& nMapMode,  
    SIZE& sizeTotal,  
    SIZE& sizePage,  
    SIZE& sizeLine) const;  
```  
  
### <a name="parameters"></a>参数  
 *nMapMode*  
 返回此视图的当前映射模式。 有关可能的值的列表，请参阅`SetScrollSizes`。  
  
 *sizeTotal*  
 设备为单位返回滚动视图的当前总大小。  
  
 *页面*  
 返回当前的水平和垂直量，以响应鼠标的每个方向滚动单击滚动条轴中。 `cx`成员包含水平的量。 `cy`成员包含垂直量。  
  
 *sizeLine*  
 返回当前的水平和垂直量，以响应鼠标的每个方向滚动单击中滚动箭头。 `cx`成员包含水平的量。 `cy`成员包含垂直量。  
  
### <a name="remarks"></a>备注  
 大小为设备单位。 很少会调用此成员函数。  
  
##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition  
 调用`GetScrollPosition`时所需的当前水平和垂直位置的滚动框在滚动条。  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 水平和垂直位置 （以逻辑单位） 的滚动框作为`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 此坐标对对应于视图的左上角已滚动到文档中的位置。  
  
 `GetScrollPosition` 返回值中的逻辑单元。 如果你希望设备单位，使用`GetDeviceScrollPosition`相反。  
  
##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize  
 调用`GetTotalSize`检索滚动视图的当前水平和垂直大小。  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 使用逻辑单位滚动视图的总大小。 水平大小为`cx`的成员`CSize`返回值。 垂直大小为`cy`成员。  
  
##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit  
 调用`ResizeParentToFit`让您视图的大小决定其框架窗口的大小。  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bShrinkOnly*  
 若要执行调整大小的类型。 默认值为 TRUE，如果相应缩小框架窗口。 对于大型视图或小型框架窗口仍将显示滚动条。 如果值为 FALSE 会导致始终要准确调整大小的框架窗口的视图。 这可能会稍有危险，因为框架窗口可能会太大，能够容纳在多文档界面 (MDI) 框架窗口或屏幕。  
  
### <a name="remarks"></a>备注  
 这被建议仅用于 MDI 子框架窗口中的视图。 使用`ResizeParentToFit`中`OnInitialUpdate`处理程序函数的派生`CScrollView`类。 有关此成员函数的示例，请参阅[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 `ResizeParentToFit` 假设已设置了视图窗口的大小。 如果视图窗口大小尚未设置何时`ResizeParentToFit`是调用，将获取断言。 若要确保，这不会发生，进行以下调用之前调用`ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition  
 调用`ScrollToPosition`滚动到视图中给定点。  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>参数  
 *pt*  
 要滚动到，逻辑单元中的点。 `x`成员必须为正值 （大于或等于 0，最大总视图的大小）。 同样适用于`y`MM_TEXT 映射模式时的成员。 `y`成员为负值 MM_TEXT 以外的映射模式下。  
  
### <a name="remarks"></a>备注  
 将滚动视图，以便这一点是窗口的左上角。 如果该视图将调整为适合必须不会调用此成员函数。  
  
##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize  
 调用`SetScaleToFitSize`当你想要自动缩放到当前窗口大小的视区大小。  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>参数  
 *sizeTotal*  
 该视图是以缩放水平和垂直大小。 滚动视图的大小以逻辑单元。 中包含的水平大小`cx`成员。 中包含的垂直大小`cy`成员。 这两`cx`和`cy`必须大于或等于 0。  
  
### <a name="remarks"></a>备注  
 带滚动条，仅为一部分的逻辑视图可能会看到在任何时间。 而与缩放以适合功能，该视图的任何滚动条，拉伸或收缩以完全适合窗口的工作区的逻辑视图。 窗口调整大小时，视图将在新的规模基于窗口的大小绘制其数据。  
  
 通常将放入到调用`SetScaleToFitSize`中的视图的重写`OnInitialUpdate`成员函数。 如果不希望自动缩放，调用`SetScrollSizes`成员函数。  
  
 `SetScaleToFitSize` 可以用于实现"缩放 Fit"操作。 使用`SetScrollSizes`重新初始化滚动。  
  
 `SetScaleToFitSize` 假设已设置了视图窗口的大小。 如果视图窗口大小尚未设置何时`SetScaleToFitSize`是调用，将获取断言。 若要确保，这不会发生，进行以下调用之前调用`SetScaleToFitSize`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes  
 调用`SetScrollSizes`视图时要进行更新。  
  
```  
void SetScrollSizes(
    int nMapMode,  
    SIZE sizeTotal,  
    const SIZE& sizePage = sizeDefault,  
    const SIZE& sizeLine = sizeDefault);
```  
  
### <a name="parameters"></a>参数  
 *nMapMode*  
 要设置此视图的映射模式。 可能的值包括：  
  
|映射模式|逻辑单元|Y 轴扩展...|  
|------------------|------------------|---------------------------------|  
|MM_TEXT|1 个像素|向下|  
|MM_HIMETRIC|0.01 毫米|向上|  
|MM_TWIPS|中的 1/1440|向上|  
|MM_HIENGLISH|0.001 英寸|向上|  
|MM_LOMETRIC|0.1 毫米|向上|  
|MM_LOENGLISH|0.01 英寸|向上|  
  
 所有这些模式都由 Windows 定义。 两种标准的映射模式，MM_ISOTROPIC 和 MM_ANISOTROPIC，不能提供`CScrollView`。 类库提供了`SetScaleToFitSize`缩放到窗口大小的视图的成员函数。 上表中的第三列描述的坐标的方向。  
  
 *sizeTotal*  
 滚动视图的总大小。 `cx`成员包含的水平范围。 `cy`成员包含垂直扩展盘区。 大小为逻辑单元。 这两`cx`和`cy`必须大于或等于 0。  
  
 *页面*  
 水平和垂直量，以响应鼠标的每个方向滚动单击滚动条轴中。 `cx`成员包含水平的量。 `cy`成员包含垂直量。  
  
 *sizeLine*  
 水平和垂直量，以响应鼠标的每个方向滚动单击滚动箭头。 `cx`成员包含水平的量。 `cy`成员包含垂直量。  
  
### <a name="remarks"></a>备注  
 调用的重写中`OnUpdate`成员函数以调整滚动特征时，例如，最初显示的文档，或在它更改大小。  
  
 您将通常大小从获取信息的视图关联的文档通过调用文档成员函数时，可能是名为`GetMyDocSize`，提供与您的派生的文档类。 下面的代码显示了这种方法：  
  
 [!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 或者，你有时可能需要设置的固定的大小，如以下代码所示：  
  
 [!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 必须设置为除 MM_ISOTROPIC 或 MM_ANISOTROPIC Windows 映射模式之一的映射模式。 如果你想要使用不受约束的映射模式下，调用`SetScaleToFitSize`成员函数而不是`SetScrollSizes`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)
