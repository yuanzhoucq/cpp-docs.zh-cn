---
title: "CScrollView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CScrollView
dev_langs:
- C++
helpviewer_keywords:
- CScrollView class
- views, scrolling
- scrolling views
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0dc937a9559306ff527779c45af9fdb62cf602df
ms.lasthandoff: 02/24/2017

---
# <a name="cscrollview-class"></a>CScrollView 类
一个[CView](../../mfc/reference/cview-class.md)带滚动功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CScrollView : public CView  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CScrollView::CScrollView](#cscrollview)|构造 `CScrollView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CScrollView::CheckScrollBars](#checkscrollbars)|指示滚动视图是否具有水平和垂直滚动条。|  
|[CScrollView::FillOutsideRect](#filloutsiderect)|填充视图是滚动区域以外的区域。|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|获取当前以设备为单位的滚动位置。|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|获取当前的映射模式、 的总大小和可滚动视图的行和页大小。 大小为以设备为单位。|  
|[CScrollView::GetScrollPosition](#getscrollposition)|获取当前使用逻辑单位的滚动位置。|  
|[CScrollView::GetTotalSize](#gettotalsize)|使用逻辑单位获取滚动视图的总大小。|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|导致要听写及其的帧的大小的视图的大小。|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|滚动到给定的点，在逻辑单元中指定的视图。|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|将置于缩放以适合模式滚动视图。|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|设置滚动视图映射模式、 总大小和水平和垂直滚动量。|  
  
## <a name="remarks"></a>备注  
 您可以处理任何派生自的类中滚动您自己的标准`CView`通过重写消息映射[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数。 但是`CScrollView`会添加以下功能对其`CView`功能︰  
  
-   它管理窗口和视区的大小以及映射模式。  
  
-   它会自动滚动以响应滚动条消息。  
  
-   它会自动滚动以响应消息从键盘、 非滚动鼠标或智能鼠标滚轮。  
  
 若要自动滚动以响应键盘消息，添加 WM_KEYDOWN 消息，并测试 VK_DOWN、 VK_PREV 和调用[SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 您可以处理鼠标滚轮滚动自己通过重写消息映射[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成员函数。 因为它们是为`CScrollView`，这些成员函数支持的建议的行为[对 WM_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617)，鼠标轮旋转消息。  
  
 若要利用自动滚动，派生视图类从`CScrollView`而不是从`CView`。 当第一次创建视图，如果您想要计算的基于文档中，调用大小的可滚动视图大小`SetScrollSizes`通过重写的成员函数[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)。 （您必须编写您自己的代码来查询文档的大小。 有关示例，请参阅[Scribble 示例](../../visual-cpp-samples.md)。)  
  
 对调用`SetScrollSizes`成员函数将设置视图的映射模式、 滚动视图和水平和垂直滚动的金额的总尺寸。 所有尺寸都都使用逻辑单位。 该视图的逻辑大小通常计算从数据存储在文档中，但在某些情况下，可能想要指定固定的大小。 有关这两种方法的示例，请参阅[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 指定以水平和垂直滚动的逻辑单元的金额。 默认情况下，如果用户单击滚动框的外部的滚动条轴`CScrollView`执行滚动操作使得"页"。 如果用户单击滚动箭头的滚动条任意一端`CScrollView`执行滚动操作使得"行"。 默认情况下，一页就是 1/10 的该视图; 的总大小线路是 1/10 的页大小。 通过传递自定义大小，以重写这些默认值`SetScrollSizes`成员函数。 例如，您可能设置的水平大小为的总大小和对行的高度的垂直大小的宽度的某些部分在当前的字体。  
  
 而不是滚动，`CScrollView`可以自动缩放视图到当前窗口的大小。 在此模式下，此视图具有任何滚动条，逻辑视图被拉伸或收缩以完全适合窗口的工作区。 若要使用此比例调整功能，请调用[CScrollView::SetScaleToFitSize](#setscaletofitsize)。 (调用`SetScaleToFitSize`或`SetScrollSizes`，但不要同时使用两者。)  
  
 之前`OnDraw`称为派生的视图类的成员函数，`CScrollView`自动进行调整的视区原点`CPaintDC`设备上下文对象，将其传递到`OnDraw`。  
  
 若要调整滚动的窗口中，视区原点`CScrollView`替代[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 这一调整是自动的`CPaintDC`设备上下文的`CScrollView`将传递给`OnDraw`，但是必须调用**CScrollView::OnPrepareDC**对任何其他设备上下文的您自己使用，如`CClientDC`。 您可以重写**CScrollView::OnPrepareDC**设置笔、 背景色和其他绘图的属性，但调用基类来进行缩放。  
  
 在以下情况中所示，可以在三个位置相对于一个视图，显示滚动条︰  
  
-   可以为视图使用设置标准的窗口样式滚动条**WS_HSCROLL**和**WS_VSCROLL**[Windows 样式](../../mfc/reference/window-styles.md)。  
  
-   滚动条控件还可以添加到包含的视图中，用例框架将转发的框架`WM_HSCROLL`和`WM_VSCROLL`框架窗口中对当前活动视图的消息。  
  
-   该框架还将转发滚动消息从`CSplitterWnd`到当前处于活动状态的拆分器窗格 （视图） 的拆分器控件。 放入[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)带共享的滚动条，`CScrollView`对象将使用共享的而不是创建其自身。  
  
 有关详细信息使用`CScrollView`，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)和[派生视图类在 MFC 中提供](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecheckscrollbarsa--cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::CheckScrollBars  
 调用此成员函数以确定滚动视图是否具有水平和垂直条形图。  
  
```  
void CheckScrollBars(
    BOOL& bHasHorzBar,  
    BOOL& bHasVertBar) const;  
```  
  
### <a name="parameters"></a>参数  
 *bHasHorzBar*  
 指示应用程序具有水平滚动条。  
  
 *bHasVertBar*  
 指示应用程序具有一个垂直滚动条。  
  
##  <a name="a-namecscrollviewa--cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView  
 构造 `CScrollView` 对象。  
  
```  
CScrollView();
```  
  
### <a name="remarks"></a>备注  
 您必须调用`SetScrollSizes`或`SetScaleToFitSize`之前滚动视图是可用。  
  
##  <a name="a-namefilloutsiderecta--cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect  
 调用`FillOutsideRect`以填充区域外滚动区域将显示的视图。  
  
```  
void FillOutsideRect(
    CDC* pDC,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 设备上下文是用来进行填充。  
  
 `pBrush`  
 画笔的区域填充是。  
  
### <a name="remarks"></a>备注  
 使用`FillOutsideRect`中滚动视图的`OnEraseBkgnd`处理程序函数，以防止过多的背景重画。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&164;](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="a-namegetdevicescrollpositiona--cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition  
 调用`GetDeviceScrollPosition`何时需要当前水平和垂直位置的滚动框中的滚动条。  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 水平和垂直位置 （以设备为单位） 的滚动框作为`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 此坐标对对应于已向其滚动视图的左上角的文档中的位置。 这是用于抵销滚动查看设备职位鼠标设备位置很有用。  
  
 `GetDeviceScrollPosition`以设备为单位返回值。 如果您希望的逻辑单元，使用`GetScrollPosition`相反。  
  
##  <a name="a-namegetdevicescrollsizesa--cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes  
 `GetDeviceScrollSizes`获取当前的映射模式、 的总大小和可滚动视图的行和页大小。  
  
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
 返回以设备为单位的滚动视图的当前总大小。  
  
 `sizePage`  
 返回当前的水平和垂直量在每个方向以响应鼠标滚动单击滚动条轴中。 **Cx**成员包含水平的量。 **Cy**成员包含垂直量。  
  
 `sizeLine`  
 返回当前的水平和垂直量在每个方向以响应鼠标滚动单击滚动箭头。 **Cx**成员包含水平的量。 **Cy**成员包含垂直量。  
  
### <a name="remarks"></a>备注  
 大小为以设备为单位。 很少会调用此成员函数。  
  
##  <a name="a-namegetscrollpositiona--cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition  
 调用`GetScrollPosition`何时需要当前水平和垂直位置的滚动框中的滚动条。  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 水平和垂直位置 （使用逻辑单位） 的滚动框作为`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 此坐标对对应于已向其滚动视图的左上角的文档中的位置。  
  
 `GetScrollPosition`返回值中的逻辑单元。 如果您希望设备单位，使用`GetDeviceScrollPosition`相反。  
  
##  <a name="a-namegettotalsizea--cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize  
 调用`GetTotalSize`要检索的滚动视图当前的水平和垂直大小。  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 使用逻辑单位的滚动视图总大小。 水平大小为**cx**的成员`CSize`返回值。 垂直大小为**cy**成员。  
  
##  <a name="a-nameresizeparenttofita--cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit  
 调用`ResizeParentToFit`让您的视图的大小指示其框架窗口的大小。  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bShrinkOnly*  
 若要执行调整大小的类型。 默认值为**TRUE**，如果相应缩小框架窗口。 对于较大视图或小型框架窗口，仍将显示滚动条。 值为**FALSE**使视图始终完全调整框架窗口的大小。 这可能会稍有危险，因为框架窗口可能会收到过大而无法容纳在多文档界面 (MDI) 框架窗口或屏幕内。  
  
### <a name="remarks"></a>备注  
 这被建议仅用于 MDI 子框架窗口中的视图。 使用`ResizeParentToFit`中`OnInitialUpdate`处理程序函数的派生`CScrollView`类。 有关此成员函数的示例，请参阅[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 `ResizeParentToFit`假定已设置了视图窗口的大小。 如果将视图的窗口大小尚未设置时`ResizeParentToFit`是调用，您将获得一个断言。 若要确保此情况发生，进行以下调用之前调用`ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView #&165;](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="a-namescrolltopositiona--cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::ScrollToPosition  
 调用`ScrollToPosition`以滚动到视图中给定的点。  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 要向下滚动到，使用逻辑单位的点。 **X**成员必须为正值 （大于或等于 0，最多的视图的总大小）。 同样适用于**y**成员映射模式时`MM_TEXT`。 **Y**成员为负以外，模式将映射`MM_TEXT`。  
  
### <a name="remarks"></a>备注  
 因此，此点窗口左上角的窗口中，将会滚动视图。 如果对视图进行缩放以适合，必须不调用该成员函数。  
  
##  <a name="a-namesetscaletofitsizea--cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize  
 调用`SetScaleToFitSize`当您想要自动缩放使视区大小与当前窗口的大小。  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>参数  
 `sizeTotal`  
 水平和垂直大小的视图是可按比例。 滚动视图大小单位逻辑单元。 中包含的水平大小**cx**成员。 中包含的垂直大小**cy**成员。 这两**cx**和**cy**必须大于或等于 0。  
  
### <a name="remarks"></a>备注  
 带滚动条，只有逻辑视图部分可能会显示在任何时间。 而进行缩放以适合功能中，此视图具有任何滚动条操作和逻辑视图被拉伸或收缩以完全适合窗口的工作区。 在窗口中调整大小时，视图在一个基于窗口的大小的新刻度绘制其数据。  
  
 通常将放入到调用`SetScaleToFitSize`的视图的重写中`OnInitialUpdate`成员函数。 如果不希望自动缩放，调用`SetScrollSizes`成员函数。  
  
 `SetScaleToFitSize`可以用于实现"缩放 Fit"操作。 使用`SetScrollSizes`若要重新初始化滚动。  
  
 `SetScaleToFitSize`假定已设置了视图窗口的大小。 如果将视图的窗口大小尚未设置时`SetScaleToFitSize`是调用，您将获得一个断言。 若要确保此情况发生，进行以下调用之前调用`SetScaleToFitSize`:  
  
 [!code-cpp[NVC_MFCDocView #&165;](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="a-namesetscrollsizesa--cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes  
 调用`SetScrollSizes`视图时要进行更新。  
  
```  
void SetScrollSizes(
    int nMapMode,  
    SIZE sizeTotal,  
    const SIZE& sizePage = sizeDefault,  
    const SIZE& sizeLine = sizeDefault);
```  
  
### <a name="parameters"></a>参数  
 `nMapMode`  
 要设置为该视图的映射模式。 可能的值包括：  
  
|映射模式|逻辑单元|正 y 轴扩展...|  
|------------------|------------------|---------------------------------|  
|`MM_TEXT`|1 个像素|向下|  
|`MM_HIMETRIC`|0.01 毫米|向上|  
|`MM_TWIPS`|中的&1;/1440|向上|  
|`MM_HIENGLISH`|0.001 英寸|向上|  
|`MM_LOMETRIC`|0.1 毫米|向上|  
|`MM_LOENGLISH`|0.01 英寸|向上|  
  
 所有这些模式都由 Windows 定义。 两种标准的映射模式，`MM_ISOTROPIC`和`MM_ANISOTROPIC`，不能使用`CScrollView`。 类库提供了`SetScaleToFitSize`缩放窗口的大小的视图的成员函数。 第三列上表中的描述的坐标的方向。  
  
 `sizeTotal`  
 滚动视图总大小。 **Cx**成员都包含有水平扩展盘区。 **Cy**成员包含垂直扩展盘区。 大小为使用逻辑单位。 这两**cx**和**cy**必须大于或等于 0。  
  
 `sizePage`  
 在滚动条轴中单击向下滚动以响应鼠标每个方向的水平和垂直金额。 **Cx**成员包含水平的量。 **Cy**成员包含垂直量。  
  
 `sizeLine`  
 水平和垂直量，以响应鼠标每个方向滚动单击滚动箭头。 **Cx**成员包含水平的量。 **Cy**成员包含垂直量。  
  
### <a name="remarks"></a>备注  
 在重写中调用它`OnUpdate`成员函数以调整滚动特征，例如，最初显示的文档或时调整大小。  
  
 您将通常大小信息从获取视图的相关文档，通过调用文档成员函数，也许称为`GetMyDocSize`，提供与您的派生的文档类。 下面的代码演示了这种方法︰  
  
 [!code-cpp[NVC_MFCDocView #&166;](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 或者，您有时可能需要设置固定的大小，如以下代码所示︰  
  
 [!code-cpp[NVC_MFCDocView #&167;](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 必须将映射模式设置为任何除 Windows 映射模式`MM_ISOTROPIC`或`MM_ANISOTROPIC`。 如果您想要使用不受约束的映射模式，则调用`SetScaleToFitSize`成员函数而不是`SetScrollSizes`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&168;](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&169;](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)

