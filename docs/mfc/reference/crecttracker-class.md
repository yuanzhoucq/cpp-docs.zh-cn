---
title: CRectTracker 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eff57e1fde0af6e794c2c47db7d1e31daf545715
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="crecttracker-class"></a>CRectTracker 类
允许要显示、 移动和不同的方式调整大小的项。  
  
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
|[CRectTracker::GetHandleMask](#gethandlemask)|调用以获取的掩码`CRectTracker`项的大小调整图柄。|  
|[CRectTracker::GetTrueRect](#gettruerect)|返回包括调整大小图柄的矩形的宽度和高度。|  
|[CRectTracker::HitTest](#hittest)|返回与相关光标的当前位置`CRectTracker`对象。|  
|[CRectTracker::NormalizeHit](#normalizehit)|规范化的命中测试代码。|  
|[CRectTracker::OnChangedRect](#onchangedrect)|调整大小矩形或将其移动时调用。|  
|[CRectTracker::SetCursor](#setcursor)|设置光标，具体取决于矩形通过其位置。|  
|[CRectTracker::Track](#track)|允许用户用来处理矩形。|  
|[Crecttracker:: Trackrubberband](#trackrubberband)|允许用户"橡皮筋"选择。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|确定大小调整大小图柄。|  
|[CRectTracker::m_nStyle](#m_nstyle)|跟踪器的当前 style(s)。|  
|[Crecttracker:: M_rect](#m_rect)|（以像素为单位） 的矩形的当前位置。|  
|[CRectTracker::m_sizeMin](#m_sizemin)|确定最小矩形宽度和高度。|  
  
## <a name="remarks"></a>备注  
 `CRectTracker` 没有基类。  
  
 尽管`CRectTracker`类旨在允许用户通过使用图形界面与 OLE 项交互，其使用并不局限于 OLE 启用应用程序。 可以使用此类用户界面是必需的任何位置。  
  
 `CRectTracker` 边框可以是实线或点线。 该项可以给出阴影的边框或叠加用阴影图案以指示不同状态的项。 你可以将八个大小调整控点放置在外部或内部上的项的边框。 (有关调整大小图柄的说明，请参阅[GetHandleMask](#gethandlemask)。)最后，`CRectTracker`允许您更改某一项在调整大小的方向。  
  
 若要使用`CRectTracker`，构造`CRectTracker`对象，并指定哪些显示状态进行初始化。 然后可以使用此接口来提供有关与关联的 OLE 项的当前状态的用户 visual 反馈`CRectTracker`对象。  
  
 有关详细信息使用`CRectTracker`，请参阅文章[跟踪器](../../mfc/trackers.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CRectTracker`  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
##  <a name="adjustrect"></a>  CRectTracker::AdjustRect  
 使用重设大小句柄调整跟踪矩形的大小时，由框架调用。  
  
```  
virtual void AdjustRect(
    int nHandle,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `nHandle`  
 使用句柄的索引。  
  
 `lpRect`  
 指向的当前大小的矩形的指针。 （矩形的大小由给定其高度和宽度。）  
  
### <a name="remarks"></a>备注  
 此函数的默认行为允许矩形的方向，若要更改时，才`Track`和`TrackRubberBand`使用反转允许调用。  
  
 重写此函数可控制在拖动操作过程中跟踪矩形的调整。 一种方法是调整指定的坐标`lpRect`在返回之前。  
  
 不直接支持的特殊功能`CRectTracker`，例如对齐到网格或保持纵横比，可以实现通过重写此函数。  
  
##  <a name="crecttracker"></a>  CRectTracker::CRectTracker  
 创建并初始化`CRectTracker`对象。  
  
```  
CRectTracker();

 
CRectTracker(
    LPCRECT lpSrcRect,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 `lpSrcRect`  
 Rectangle 对象的坐标。  
  
 `nStyle`  
 指定的样式`CRectTracker`对象。 支持以下样式：  
  
- **CRectTracker::solidLine**实线用于矩形边框。  
  
- **CRectTracker::dottedLine**矩形边框所使用点线。  
  
- **CRectTracker::hatchedBorder**矩形边框所使用的阴影的模式。  
  
- **CRectTracker::resizeInside**大小调整图柄位于矩形内。  
  
- **CRectTracker::resizeOutside**大小调整图柄位于外部矩形。  
  
- **CRectTracker::hatchInside** Hatched 模式涵盖整个矩形。  
  
### <a name="remarks"></a>备注  
 默认构造函数初始化`CRectTracker`对象的值从`lpSrcRect`并初始化其他大小为系统默认值。 如果对象创建不带任何参数，`m_rect`和`m_nStyle`数据成员是未初始化。  
  
##  <a name="draw"></a>  CRectTracker::Draw  
 调用此函数可绘制矩形的外部直线和内部区域。  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 在其上绘制的设备上下文的指针。  
  
### <a name="remarks"></a>备注  
 跟踪器样式确定如何绘制。 请参阅的构造函数`CRectTracker`有关详细信息可用的样式。  
  
##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect  
 每当跟踪器的位置已更改时由框架调用内而`Track`或`TrackRubberBand`成员函数。  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`，其中包含要绘制的矩形。  
  
 `pWndClipTo`  
 指向窗口用于剪辑矩形的指针。  
  
 `pDC`  
 在其上绘制的设备上下文的指针。  
  
 `pWnd`  
 指向将在其绘制窗口的指针。  
  
### <a name="remarks"></a>备注  
 默认实现将调用`CDC::DrawFocusRect`，绘制的虚线的矩形。  
  
 重写此函数可在跟踪操作期间提供不同的反馈。  
  
##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask  
 框架调用此成员函数可为矩形的大小调整图柄检索掩码。  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>返回值  
 掩码`CRectTracker`项的大小调整图柄。  
  
### <a name="remarks"></a>备注  
 调整大小图柄显示在侧和矩形的角变，并允许用户控制的形状和矩形的大小。  
  
 矩形具有 8 调整大小图柄编号为 0-7。 每个重设大小句柄表示的位掩码; 中该位的值为 2 ^ *n*，其中*n*是重设大小句柄数。 位 0-3 对应于角调整大小图柄，开始向左上角移动顺时针旋转。 Bits 4-7 对应于端调整大小图柄沿顺时针方向移动顶部开始。 下图显示矩形的大小调整处理并及其相应的调整大小控点的数量和值：  
  
 ![调整大小控点的数量](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 默认实现**GetHandleMask**返回的位掩码，以便显示大小调整控点。 如果一个位是打开的则将绘制相应的重设大小句柄。  
  
 重写该成员函数以隐藏或显示指示的大小调整图柄。  
  
##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect  
 调用此函数可检索的矩形的坐标。  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpTrueRect`  
 指向`RECT`结构，它将包含设备坐标`CRectTracker`对象。  
  
### <a name="remarks"></a>备注  
 矩形的尺寸包括的高度和宽度的位于外部边框任何调整大小图柄。 在返回，`lpTrueRect`是始终在设备坐标的规范化的矩形。  
  
##  <a name="hittest"></a>  CRectTracker::HitTest  
 调用此函数可了解用户是否具有只张开重设大小句柄。  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>参数  
 `point`  
 在设备坐标中，若要测试的点。  
  
### <a name="return-value"></a>返回值  
 基于枚举类型，则返回该值**CRectTracker::TrackerHit**和可以具有以下值之一：  
  
- **CRectTracker::hitNothing** -1  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize  
 大小，以像素为单位的`CRectTracker`大小调整图柄。  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>备注  
 初始化使用默认系统值。  
  
##  <a name="m_rect"></a>  Crecttracker:: M_rect  
 在工作区坐标 （像素） 的矩形的当前位置。  
  
```  
CRect m_rect;  
```  
  
##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin  
 矩形最小大小。  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>备注  
 这两个默认值， **cx**和**cy**，计算出的边框宽度的默认系统值。 此数据成员仅供`AdjustRect`成员函数。  
  
##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle  
 在该矩形的当前样式。  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>备注  
 请参阅[CRectTracker::CRectTracker](#crecttracker)有关的可能的样式列表。  
  
##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit  
 调用此函数可将转换可能倒句柄。  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>参数  
 `nHandle`  
 由用户选择的句柄。  
  
### <a name="return-value"></a>返回值  
 规范化的句柄的索引。  
  
### <a name="remarks"></a>备注  
 当`CRectTracker::Track`或`CRectTracker::TrackRubberBand`调用与反转允许，则可能要反转 x 轴和 / 或 y 轴上的矩形。 在此情况下，`HitTest`将返回还反转方面矩形的句柄。 这是不适合于绘制光标反馈，因为反馈取决于矩形，不将进行相应修改矩形数据结构的部分的屏幕位置。  
  
##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect  
 由框架调用，每当在调用已更改跟踪器矩形`Track`。  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>参数  
 *rectOld*  
 包含的旧设备坐标`CRectTracker`对象。  
  
### <a name="remarks"></a>备注  
 在时间调用此函数，所有反馈绘制`DrawTrackerRect`已删除。 此函数的默认实现不执行任何操作。  
  
 当你想要调整大小矩形后执行任何操作时，重写此函数。  
  
##  <a name="setcursor"></a>  CRectTracker::SetCursor  
 调用此函数可将光标形状改而悬停`CRectTracker`对象的区域。  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向当前包含光标的窗口。  
  
 `nHitTest`  
 以前的命中测试的结果从`WM_SETCURSOR`消息。  
  
### <a name="return-value"></a>返回值  
 如果上一命中结果是通过跟踪器矩形中; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数在你处理的窗口函数内部`WM_SETCURSOR`消息 (通常`OnSetCursor`)。  
  
##  <a name="track"></a>  CRectTracker::Track  
 调用此函数可显示调整矩形大小的用户界面。  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 包含矩形的窗口对象。  
  
 `point`  
 设备坐标，相对于工作区的当前鼠标位置。  
  
 `bAllowInvert`  
 如果**TRUE**，矩形可倒沿 x 轴或 y 轴; 否则为**FALSE**。  
  
 `pWndClipTo`  
 绘制操作将剪切到窗口。 如果**NULL**，`pWnd`用作的剪辑矩形。  
  
### <a name="return-value"></a>返回值  
 如果按 ESC 键，跟踪进程将暂停，不更改跟踪器中存储的矩形，并返回 0。 如果则会提交更改，通过将鼠标并释放鼠标左键，新的位置和/或大小在中记录跟踪器的矩形，并返回非零。  
  
### <a name="remarks"></a>备注  
 这通常从内部处理你应用程序的函数调用`WM_LBUTTONDOWN`消息 (通常`OnLButtonDown`)。  
  
 此函数将捕获鼠标，直到用户释放鼠标左键、 按 ESC 键，或按下鼠标右键按钮。 当用户将鼠标光标，通过调用更新反馈`DrawTrackerRect`和`OnChangedRect`。  
  
 如果`bAllowInvert`是**TRUE**，跟踪矩形可以反转 x 轴或 y 轴上。  
  
##  <a name="trackrubberband"></a>  Crecttracker:: Trackrubberband  
 调用此函数可执行橡皮筋选择。  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 包含矩形的窗口对象。  
  
 `point`  
 设备坐标，相对于工作区的当前鼠标位置。  
  
 `bAllowInvert`  
 如果**为 TRUE，**矩形可倒沿 x 轴或 y 轴; 否则为**FALSE**。  
  
### <a name="return-value"></a>返回值  
 如果鼠标已移动，以及在该矩形不为空; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 它通常从内部处理你应用程序的函数调用`WM_LBUTTONDOWN`消息 (通常`OnLButtonDown`)。  
  
 此函数将捕获鼠标，直到用户释放鼠标左键、 按 ESC 键，或按下鼠标右键按钮。 当用户将鼠标光标，通过调用更新反馈`DrawTrackerRect`和`OnChangedRect`。  
  
 跟踪将执行，并从右下角的句柄橡皮带类型选择。 如果允许反转，可以通过拖动是向上和向左或向下和向右大小调整矩形。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例跟踪器](../../visual-cpp-samples.md)   
 [MFC 示例 DRAWCLI](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleResizeBar 类](../../mfc/reference/coleresizebar-class.md)   
 [CRect 类](../../atl-mfc-shared/reference/crect-class.md)
