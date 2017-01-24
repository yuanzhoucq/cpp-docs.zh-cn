---
title: "CScrollView Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CScrollView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CScrollView class"
  - "scrolling views"
  - "视图, 滚动"
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CScrollView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CView](../../mfc/reference/cview-class.md) 以滚动功能。  
  
## 语法  
  
```  
class CScrollView : public CView  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CScrollView::CScrollView](../Topic/CScrollView::CScrollView.md)|构造 `CScrollView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CScrollView::CheckScrollBars](../Topic/CScrollView::CheckScrollBars.md)|指示滚动视图是否有水平和垂直滚动条。|  
|[CScrollView::FillOutsideRect](../Topic/CScrollView::FillOutsideRect.md)|加载视图区域中移动的范围之外的。|  
|[CScrollView::GetDeviceScrollPosition](../Topic/CScrollView::GetDeviceScrollPosition.md)|获取在组件单位的当前滚动位置。|  
|[CScrollView::GetDeviceScrollSizes](../Topic/CScrollView::GetDeviceScrollSizes.md)|获取当前映射模式、总大小和一个滚动视图的行和页大小。  范围在组件度量单位。|  
|[CScrollView::GetScrollPosition](../Topic/CScrollView::GetScrollPosition.md)|获取在逻辑单位的当前滚动位置。|  
|[CScrollView::GetTotalSize](../Topic/CScrollView::GetTotalSize.md)|获取滚动视图的总大小\(以逻辑单位的。|  
|[CScrollView::ResizeParentToFit](../Topic/CScrollView::ResizeParentToFit.md)|导致视图的范围指定其帧的大小。|  
|[CScrollView::ScrollToPosition](../Topic/CScrollView::ScrollToPosition.md)|在逻辑单位滚动视图对给定的点，指定。|  
|[CScrollView::SetScaleToFitSize](../Topic/CScrollView::SetScaleToFitSize.md)|放入滚动到视图缩放以适应模式。|  
|[CScrollView::SetScrollSizes](../Topic/CScrollView::SetScrollSizes.md)|将滚动视图的映射模式，总大小，并且，水平和垂直滚动量。|  
  
## 备注  
 您可以处理标准滚动从 `CView` 任何派生类的选件通过重写消息映射的 [OnHScroll](../Topic/CWnd::OnHScroll.md) 和 [OnVScroll](../Topic/CWnd::OnVScroll.md) 成员函数。  但是，`CScrollView` 将下列功能添加到其 `CView` 功能:  
  
-   它管理窗口和视区大小和映射方案。  
  
-   它会自动将响应滚动条消息。  
  
-   它会自动将响应从键盘、非滚动鼠标滚轮或IntelliMouse的消息。  
  
 自动滚动以响应从键盘消息，添加WM\_KEYDOWN消息和测试VK\_DOWN，VK\_PREV和调用 [SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 通过重写消息映射的 [OnMouseWheel](../Topic/CWnd::OnMouseWheel.md) 和 [OnRegisteredMouseWheel](../Topic/CWnd::OnRegisteredMouseWheel.md) 成员可以处理鼠标滚轮滚动功能。  当它们供 `CScrollView`，这些成员函数支持 [WM\_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617)建议的行为，轮旋转消息。  
  
 若要利用自动滚动，从 `CScrollView` 派生您的视图选件类而不是从 `CView`。  在视图首次创建时，因此，如果要计算基于文档的大小与滚动视图的范围，请调用从 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 或 [CView::OnUpdate](../Topic/CView::OnUpdate.md)重写中 `SetScrollSizes` 成员函数。  （必须编写自己查询文档的大小自己的代码。  有关示例，请参见 [SCRIBBLE示例](../../top/visual-cpp-samples.md)。）  
  
 为 `SetScrollSizes` 成员函数的调用将视图的映射架构、滚动视图的总尺寸和沿水平和垂直滚动。  所有范围在逻辑单元。  视图的逻辑范围从存储在文档中的数据通常计算，但是，您可以在某些情况下若要指定固定大小。  以两种方法的示例，请参见 [CScrollView::SetScrollSizes](../Topic/CScrollView::SetScrollSizes.md)。  
  
 您垂直在逻辑单位指定为水平移动和。  默认情况下，因此，如果用户单击一个滚动条轴在滚动框外，`CScrollView` 移动“页”。如果用户单击卷动箭头滚动条的任一端，`CScrollView` 移动一“行”。默认情况下，页是1\/10视图的总大小;行是1\/10页大小。  通过在 `SetScrollSizes` 成员函数的自定义范围重写这些默认值。  例如，可以将该级别的范围到总大小并将垂直大小的宽度的某个部分到一行的高度在当前字体的。  
  
 而不是滚动，`CScrollView` 可以自动缩放视图到当前窗口大小。  在此模式下，视图没有滚动条，而逻辑视图拉伸或收缩正确地适应窗口的工作区。  若要使用此缩放以适应功能，请调用 [CScrollView::SetScaleToFitSize](../Topic/CScrollView::SetScaleToFitSize.md)。  （调用 `SetScaleToFitSize` 或 `SetScrollSizes`，但不能同时定义两者。）  
  
 在派生的视图选件类的 `OnDraw` 成员函数调用之前，`CScrollView` 为其传递给 `OnDraw`的 `CPaintDC` 设备上下文对象自动调整视区原点。  
  
 用于滚动窗口中调整视区原点，`CScrollView` 重写 [CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)。  这种调整为 `CScrollView` 传递给 `OnDraw`的 `CPaintDC` 设备上下文是自动的，但是，必须调用 **CScrollView::OnPrepareDC** 使用的任何其他设备上下文\(例如，`CClientDC`。  您可以重写 **CScrollView::OnPrepareDC** 设置钢笔、背景色和其他绘图特性，但是，调用基类执行缩放。  
  
 如下面用例所示，滚动条能应用于三个位置显示相对于视图，例如:  
  
-   使用 **WS\_HSCROLL** 和 **WS\_VSCROLL**[Windows样式](../../mfc/reference/window-styles.md)，标准窗口样式滚动条可以为视图设置。  
  
-   滚动条控件还能添加到包含视图的框架，框架向前 `WM_HSCROLL` 和 `WM_VSCROLL` 消息从框架窗口到为当前活动的视图情况下。  
  
-   框架向前还将从 `CSplitterWnd` 拆分控件的消息至此有效的拆分窗格\(视图）。  在放置在与具有滚动条的 [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)，`CScrollView` 对象将使用共享部分而不是创建它的属性。  
  
 有关使用 `CScrollView`的更多信息，请参见 [文档\/视图结构](../../mfc/document-view-architecture.md) 和 [派生的视图选件类可在MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例DIBLOOK](../../top/visual-cpp-samples.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)