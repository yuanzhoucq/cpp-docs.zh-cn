---
title: CScrollView 类 |Microsoft 文档
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
ms.openlocfilehash: 82ffdb26c5766a0ff7cbada511c9bc9c82ebfd93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cscrollview-class"></a>CScrollView 类
A [CView](../../mfc/reference/cview-class.md)带滚动功能。  
  
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
|[CScrollView::FillOutsideRect](#filloutsiderect)|填充滚动区之外的视图的区域。|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|获取当前以设备为单位的滚动位置。|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|获取当前的映射模式、 的总大小和可滚动视图的行和页大小。 大小是以设备为单位。|  
|[CScrollView::GetScrollPosition](#getscrollposition)|获取当前逻辑单位的滚动位置。|  
|[CScrollView::GetTotalSize](#gettotalsize)|获取滚动视图的总大小中逻辑单元。|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|会导致要规定及其的帧的大小的视图大小。|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|滚动到给定的点，在逻辑单元中指定的视图。|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|将置于缩放到合适大小模式的滚动视图。|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|设置滚动视图的映射模式、 总大小和水平和垂直滚动金额。|  
  
## <a name="remarks"></a>备注  
 你可以处理任何派生自的类中滚动自己的标准`CView`通过重写消息映射[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数。 但是`CScrollView`到了以下功能其`CView`功能：  
  
-   它管理窗口和视区大小和映射模式。  
  
-   它自动滚动以响应滚动条消息。  
  
-   它自动滚动以响应从键盘、 非滚动鼠标或智能鼠标滚轮的消息。  
  
 若要自动滚动以响应从键盘消息，添加 WM_KEYDOWN 消息，以及测试 VK_DOWN、 VK_PREV 和调用[SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 你可以处理鼠标滚轮滚动自己通过重写消息映射[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成员函数。 因此`CScrollView`，这些成员函数支持的建议的行为[WM_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617)，鼠标轮旋转消息。  
  
 若要利用自动滚动，派生视图类从`CScrollView`而不是从`CView`。 视图首先创建时，如果你想要计算的大小基于文档，调用的大小的可滚动视图`SetScrollSizes`通过下列任一工具的重写成员函数[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)。 （你必须编写你自己的代码以查询文档的大小。 有关示例，请参阅[Scribble 示例](../../visual-cpp-samples.md)。)  
  
 调用`SetScrollSizes`成员函数设置的视图映射模式、 滚动视图和的金额水平或垂直地滚动的总尺寸。 所有大小都是在逻辑单元。 该视图的逻辑大小通常计算从数据存储在文档中，但在某些情况下你可能想要指定固定的大小。 有关这两种方法的示例，请参阅[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 指定在逻辑单元中滚动水平和垂直的金额。 默认情况下，如果用户单击滚动条轴滚动框的外部`CScrollView`滚动"页"。 如果用户单击滚动箭头的滚动条，任意一端`CScrollView`滚动"行"。 默认情况下，页为 1/10 的视图; 的总大小行是 1/10 的页大小。 通过传递自定义大小，以重写这些默认值`SetScrollSizes`成员函数。 例如，你可能的水平大小设置为的总大小和到行的高度的垂直大小的宽度的某些部分在当前的字体。  
  
 而不是滚动，`CScrollView`可以自动缩放到当前窗口的大小的视图。 在此模式下，此视图具有任何滚动条和逻辑视图被拉伸或收缩以完全适合窗口的工作区。 若要使用此横向调整功能，调用[CScrollView::SetScaleToFitSize](#setscaletofitsize)。 (调用`SetScaleToFitSize`或`SetScrollSizes`，但不是两者。)  
  
 之前`OnDraw`调用的派生的视图类的成员函数时，`CScrollView`自动调整的视区原点`CPaintDC`设备上下文对象，它将传递给`OnDraw`。  
  
 若要调整滚动的窗口中，视区原点`CScrollView`重写[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 此调整是自动的`CPaintDC`设备上下文的`CScrollView`将传递给`OnDraw`，但必须调用**CScrollView::OnPrepareDC**用于任何其他设备上下文的您自己使用，如`CClientDC`. 您可以重写**CScrollView::OnPrepareDC**设置钢笔、 背景色和其他绘制的特性，但调用基类来进行缩放。  
  
 在以下情况下所示，滚动条可以出现在相对于工作视图中，以下三个位置：  
  
-   可以为视图使用设置标准的窗口样式滚动条**WS_HSCROLL**和**WS_VSCROLL**[Windows 样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
-   滚动条控件还可以添加到框架，其中包含的视图中，用例框架将转发`WM_HSCROLL`和`WM_VSCROLL`当前处于活动状态的查看从框架窗口的消息。  
  
-   框架还将转发滚动消息从`CSplitterWnd`到当前处于活动状态的拆分窗格 （视图） 的拆分器控件。 在放置在时[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)带共享的滚动条，`CScrollView`对象将使用共享的而不是无需创建其自身。  
  
 有关详细信息使用`CScrollView`，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)和[派生视图类 MFC 中可用](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars  
 调用此成员函数可确定滚动视图是否具有水平和垂直条。  
  
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
 调用`FillOutsideRect`以填充区域的滚动区之外显示的视图。  
  
```  
void FillOutsideRect(
    CDC* pDC,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 是用进行填充的设备上下文。  
  
 `pBrush`  
 区域与之要填充的画笔。  
  
### <a name="remarks"></a>备注  
 使用`FillOutsideRect`中滚动视图的`OnEraseBkgnd`处理程序函数，以防止过多背景重新绘制。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition  
 调用`GetDeviceScrollPosition`时需要的当前水平和垂直位置的滚动框中的滚动条。  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 水平和垂直位置 （以设备为单位） 的滚动框作为`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 此坐标对对应于已向其滚动视图的左上角的文档中的位置。 这可用于抵销到滚动视图设备位置的鼠标设备位置。  
  
 `GetDeviceScrollPosition` 以设备单位返回值。 如果你想逻辑单元，使用`GetScrollPosition`相反。  
  
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
 `nMapMode`  
 返回此视图的当前映射模式。 有关可能的值的列表，请参阅`SetScrollSizes`。  
  
 `sizeTotal`  
 以设备单位返回当前的总大小的滚动视图。  
  
 `sizePage`  
 返回当前的水平和垂直金额，才可在响应鼠标每个方向上滚动单击滚动条轴中。 **Cx**成员包含水平的量。 **Cy**成员包含垂直的量。  
  
 `sizeLine`  
 返回当前的水平和垂直金额，才可在响应鼠标每个方向上滚动单击滚动箭头。 **Cx**成员包含水平的量。 **Cy**成员包含垂直的量。  
  
### <a name="remarks"></a>备注  
 大小是以设备为单位。 极少数情况下调用此成员函数。  
  
##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition  
 调用`GetScrollPosition`时需要的当前水平和垂直位置的滚动框中的滚动条。  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 水平和垂直位置 （以逻辑单位） 的滚动框作为`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 此坐标对对应于已向其滚动视图的左上角的文档中的位置。  
  
 `GetScrollPosition` 在逻辑单元中返回值。 如果你希望设备单位，使用`GetDeviceScrollPosition`相反。  
  
##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize  
 调用`GetTotalSize`检索滚动视图的当前水平和垂直大小。  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滚动视图逻辑单位的总大小。 水平大小为**cx**的成员`CSize`返回值。 垂直大小为**cy**成员。  
  
##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit  
 调用`ResizeParentToFit`让你的视图的大小决定其框架窗口的大小。  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bShrinkOnly*  
 若要执行调整大小的类型。 默认值， **TRUE**，根据收缩框架窗口。 滚动条仍将显示为大型视图或小框架窗口。 值为**FALSE**使视图始终完全调整框架窗口的大小。 这可能会稍有危险，因为框架窗口无法获取太大，无法容纳在多文档界面 (MDI) 框架窗口或屏幕内。  
  
### <a name="remarks"></a>备注  
 这被建议仅对 MDI 子框架窗口中的视图。 使用`ResizeParentToFit`中`OnInitialUpdate`的你派生的处理程序函数`CScrollView`类。 有关此成员函数的示例，请参阅[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 `ResizeParentToFit` 假定已设置了视图窗口的大小。 如果视图窗口大小尚未设置时`ResizeParentToFit`是调用，将获取断言。 若要确保此情况发生，进行以下调用之前调用`ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition  
 调用`ScrollToPosition`以滚动到视图中给定的点。  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 要向下滚动到，在逻辑单元的点。 **X**成员必须是一个正值 （大于或等于 0，直到达到总大小的视图）。 同样适用于**y**成员映射模式时`MM_TEXT`。 **Y**成员为负以外映射模式`MM_TEXT`。  
  
### <a name="remarks"></a>备注  
 将滚动视图，以便此点位于窗口的左上角。 如果对视图进行缩放以适合不得调用此成员函数。  
  
##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize  
 调用`SetScaleToFitSize`如果想要自动缩放使视区大小与当前的窗口大小。  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>参数  
 `sizeTotal`  
 水平和垂直大小的视图是可按比例。 滚动视图的大小的单位为逻辑单元。 中包含的水平大小**cx**成员。 中包含的垂直大小**cy**成员。 同时**cx**和**cy**必须大于或等于 0。  
  
### <a name="remarks"></a>备注  
 带滚动条，仅为一部分的逻辑视图可能会显示在任何时间。 而具有缩放调整功能，该视图的任何滚动条，逻辑视图被拉伸或收缩以完全适合窗口的工作区。 调整窗口大小时，视图在一个基于窗口的大小的新刻度绘制其数据。  
  
 通常将放入到调用`SetScaleToFitSize`的视图的重写中`OnInitialUpdate`成员函数。 如果您不希望自动缩放，调用`SetScrollSizes`成员函数。  
  
 `SetScaleToFitSize` 可用来实现"缩放 Fit"操作。 使用`SetScrollSizes`重新初始化滚动。  
  
 `SetScaleToFitSize` 假定已设置了视图窗口的大小。 如果视图窗口大小尚未设置时`SetScaleToFitSize`是调用，将获取断言。 若要确保此情况发生，进行以下调用之前调用`SetScaleToFitSize`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes  
 调用`SetScrollSizes`即将更新视图时。  
  
```  
void SetScrollSizes(
    int nMapMode,  
    SIZE sizeTotal,  
    const SIZE& sizePage = sizeDefault,  
    const SIZE& sizeLine = sizeDefault);
```  
  
### <a name="parameters"></a>参数  
 `nMapMode`  
 要为此视图设置的映射模式。 可能的值包括：  
  
|映射模式|逻辑单元|正 y 轴扩展...|  
|------------------|------------------|---------------------------------|  
|`MM_TEXT`|1 个像素|向下|  
|`MM_HIMETRIC`|0.01 毫米|向上|  
|`MM_TWIPS`|中的 1/1440|向上|  
|`MM_HIENGLISH`|0.001 英寸|向上|  
|`MM_LOMETRIC`|0.1 mm|向上|  
|`MM_LOENGLISH`|0.01 中|向上|  
  
 由 Windows 定义所有这些模式。 两种标准的映射模式，`MM_ISOTROPIC`和`MM_ANISOTROPIC`，不能使用`CScrollView`。 类库提供了`SetScaleToFitSize`缩放到窗口大小的视图的成员函数。 第三列上表中的描述的坐标的方向。  
  
 `sizeTotal`  
 滚动视图总大小。 **Cx**成员包含水平扩展盘区。 **Cy**成员包含垂直扩展盘区。 大小是在逻辑单元。 同时**cx**和**cy**必须大于或等于 0。  
  
 `sizePage`  
 水平和垂直金额，才可在响应鼠标每个方向上滚动单击滚动条轴中。 **Cx**成员包含水平的量。 **Cy**成员包含垂直的量。  
  
 `sizeLine`  
 水平和垂直金额，才可在响应鼠标每个方向上滚动单击滚动箭头。 **Cx**成员包含水平的量。 **Cy**成员包含垂直的量。  
  
### <a name="remarks"></a>备注  
 在重写中调用它`OnUpdate`成员函数时，例如，最初显示的文档，或如果它更改大小调整滚动特征。  
  
 你将通常大小从获取信息的视图关联的文档通过调用文档成员函数时，可能是调用`GetMyDocSize`，提供与您的派生的文档类。 下面的代码演示此方法：  
  
 [!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 或者，你有时可能需要设置的固定的大小，如以下代码所示：  
  
 [!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 你必须将映射模式设置为任何除 Windows 映射模式`MM_ISOTROPIC`或`MM_ANISOTROPIC`。 如果你想要使用不受约束的映射模式，调用`SetScaleToFitSize`成员函数而不是`SetScrollSizes`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)
