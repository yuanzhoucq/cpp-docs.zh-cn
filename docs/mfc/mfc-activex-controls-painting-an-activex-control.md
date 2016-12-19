---
title: "MFC ActiveX 控件：绘制 ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件, 优化"
  - "MFC ActiveX 控件, 绘制"
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：绘制 ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述了 ActiveX 控件绘制进程，以及如何改变绘制代码优化过程。（参见 [优化控件绘制](../mfc/optimizing-control-drawing.md) 有关技术如何让优化绘制没有控件，单独还原以前选定的 GDI 对象。  在所有控件绘制之后，容器可以自动还原原始对象。\)  
  
 本文的示例是从用默认设置的 MFC ActiveX 控件向导创建的控件。  有关使用MFC ActiveX控件向导创建主干控件应用程序的更多信息，请参见文章 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 包含以下主题：  
  
-   [全进程绘制由 ActiveX 控件向导创建的控件和代码去支持绘制](#_core_the_painting_process_of_an_activex_control)  
  
-   [如何优化绘制进程](#_core_optimizing_your_paint_code)  
  
-   [如何使用元文件绘制你的控件](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a> ActiveX 控件的绘图进程  
 当 ActiveX 控件最初显示或重新绘制时，他们遵循和其他使用MFC开发的应用程序一样的绘制进程。开发的其他应用程序，一个重要区别：ActiveX 控件可能处于活动或非活动状态。  
  
 活动控件是通过子窗口在 ActiveX 控件容器中绘制。  像其他 Windows，当 `WM_PAINT` 消息被接收时，它负责绘制它们。  控件的基类，[COleControl](../mfc/reference/colecontrol-class.md),在它们的 `OnPaint` 函数中处理消息。  此默认实现调用控件的 `OnDraw` 函数。  
  
 非活动控件绘制是不同的。  当控件不活动，它的窗口也是不可见或不存在的，因此，它无法接收绘制消息。  相反，控件容器直接调用控件的 `OnDraw` 函数。  这与活动控件的绘图进程不同因为 `OnPaint` 成员函数从不调用。  
  
 如前面讨论所述，ActiveX 控件如何更新取决于控件的状态。  但是，由于在这两种情况下，框架调用 `OnDraw` 成员函数，你需要添加大部分绘图代码在这个成员函数中。  
  
 `OnDraw` 成员函数处理控件绘制。  当控件不活动时，控件容器调用 `OnDraw`，传递控件容器的设备上下文和由控件占有的矩形区域的坐标。  
  
 矩形传递框架到 `OnDraw` 成员函数包含控件占用的区域。  如果控件是活动的，左上角为 \(0，0\)，并将传递的设备上下文用于包含控件的子窗口。  如果控件要停用，左上角坐标不一定为 \(0，0\)，并将传递的的设备上下文用于包含控件的控件容器。  
  
> [!NOTE]
>  重要的是`OnDraw` 的修改不取决于矩形的左上角的点与 \(0，0\)相等，并只在矩形内绘制传递给 `OnDraw`。  如果超出矩形的区域外，将会发生意外的结果。  
  
 在控件实现文件 \(.cpp\)中 MFC ActiveX 控件向导提供的默认实现，如下所示，使用一个白色的画笔画矩形并用当前背景色填充椭圆。  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/CPP/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  在绘制控件时，您不应对将作为 *pdc*参数传递给 `OnDraw` 函数设备上下文状态作出假设。  偶尔容器应用程序供应设备上下文，并且不必初始化为默认状态。  特别是，显式选择画笔、钢笔、颜色、字体以及绘图代码依赖的其他资源。  
  
##  <a name="_core_optimizing_your_paint_code"></a> 优化你的绘制代码  
 在控件已成功绘制自己之后，下一步将优化 `OnDraw` 函数。  
  
 ActiveX 控件绘图的默认实现是绘制整个控件区域。  对于简单控件就足够了，但大多数情况下重新绘制控件更快，如果需要更新绘制的部分，而非整个控件。  
  
 `OnDraw` 函数是通过传递 `rcInvalid`提供一个简单的优化方法，需要绘制矩形控件的区域。  使用这个区域，通常小于整个控件区域，加速绘制进程。  
  
##  <a name="_core_painting_your_control_using_metafiles"></a> 使用元文件绘制控件  
 在许多情况下 `pdc` 参数到 `OnDraw`函数指向屏幕设备上下文（DC）。  但是，当控件在打印的图像或在"打印预览版会话期间，为呈现接收的 DC 是称为“元文件 DC”的特定类型。  与屏幕 DC不同，迅速处理发送给它的请求，元文件 DC 存储请求稍后回放。  一些容器应用程序在设计模式中还可能选择使用元文件 DC控件呈现控件图像。  
  
 图元文件绘制请求可以使用容器通过接口函数：**IViewObject::Draw** \(此函数可以被调用用于非绘制图元文件绘制\) 和 **IDataObject::GetData**被实现。  当元文件 DC 作为参数之一传递时，MFC 框架调用 [COleControl::OnDrawMetafile](../Topic/COleControl::OnDrawMetafile.md)。  由于这是一个虚成员函数，在控件类中重写这个函数执行任何特殊的进程。  默认行为调用  `COleControl::OnDraw`.。  
  
 要确定控件能在屏幕和元文件设备上下文中被绘制，你必须使用同时被屏幕和元文件 DC所支持只有一个成员的函数。  注意坐标系不能以像素为单位测量。  
  
 因为 `OnDrawMetafile` 的默认实现调用控件的 `OnDraw` 函数，请使用元文件和屏幕设备上下文都适合的成员函数，除非重写 `OnDrawMetafile`。  下面列出了可以在元文件和屏幕设备上下文中使用的 `CDC` 成员函数的子集。  有关这些功能的更多信息，请参见类 [CDC](../mfc/reference/cdc-class.md) 在 *MFC Reference*中。  
  
|弧形|BibBlt|弦形|  
|--------|------------|--------|  
|**椭圆形**|**转义符**|`ExcludeClipRect`|  
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|  
|`LineTo`|`MoveTo`|`OffsetClipRgn`|  
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|  
|`Pie`|**Polygon**|`Polyline`|  
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|  
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|  
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|  
|`SelectPalette`|`SetBkColor`|`SetBkMode`|  
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|  
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|  
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|  
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|  
|`StretchBlt`|`TextOut`||  
  
 除了 `CDC` 成员函数，有一些其他的函数在元文件 DC 中兼容。  这些包括 [CPalette::AnimatePalette](../Topic/CPalette::AnimatePalette.md), [CFont::CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md),  `CBrush`: [CreateBrushIndirect](../Topic/CBrush::CreateBrushIndirect.md) 的三个成员函数, [CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md), 和 [CreatePatternBrush](../Topic/CBrush::CreatePatternBrush.md).  
  
 在元文件中没有被记录的函数包括：[DrawFocusRect](../Topic/CDC::DrawFocusRect.md), [DrawIcon](../Topic/CDC::DrawIcon.md), [DrawText](../Topic/CDC::DrawText.md), [ExcludeUpdateRgn](../Topic/CDC::ExcludeUpdateRgn.md), [FillRect](../Topic/CDC::FillRect.md), [FrameRect](../Topic/CDC::FrameRect.md), [GrayString](../Topic/CDC::GrayString.md), [InvertRect](../Topic/CDC::InvertRect.md), [ScrollDC](../Topic/CDC::ScrollDC.md), 和 [TabbedTextOut](../Topic/CDC::TabbedTextOut.md).  由于元文件 DC 实际上与设备无关，你不能使用 SetDIBits、GetDIBits 和 CreateDIBitmap 和元文件 DC。  可以使用 SetDIBitsToDevice 和 StretchDIBits 与元文件 DC 为目标。  [CreateCompatibleDC](../Topic/CDC::CreateCompatibleDC.md)、[CreateCompatibleBitmap](../Topic/CBitmap::CreateCompatibleBitmap.md)[CreateDiscardableBitmap](../Topic/CBitmap::CreateDiscardableBitmap.md) 和无意义的元文件 DC。  
  
 在使用元文件 DC 时要考虑的另一点是坐标系不能以像素为单位测量。  为此,所有的绘制代码应该调整为适合矩形传递 `rcBounds` 在 `OnDraw` 参数中。  因为 `rcBounds` 表示控制窗口的大小，这防止控件外部的意外绘制。  
  
 在实现控件的元文件后呈现后，请使用测试容器测试元文件。  有关如何访问测试容器的信息，请参见[用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)。  
  
#### 使用测试容器，测试控件的元文件  
  
1.  在测试容器的 **编辑** 菜单上，单击 **Insert New Control**。  
  
2.  在 **Insert New Control** 框中，选择控件并单击 **确定**。  
  
     控件将出现在测试容器中。  
  
3.  在 **控件** 菜单上，单击 **Draw Metafile**。  
  
     单独窗口显示在元文件被展示的地方。  可以更改此窗口大小以查看缩放如何影响控件的元文件。  你可以随时关闭这个Window。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)