---
title: MFC ActiveX 控件：绘制 ActiveX 控件
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: fd98af90e86b6b98a856e633e50c5bf266cc466a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364584"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC ActiveX 控件：绘制 ActiveX 控件

本文描述了 ActiveX 控件绘制进程，以及如何改变绘制代码来优化过程。 （请参阅[优化控件绘图](../mfc/optimizing-control-drawing.md)，了解如何通过不单独还原以前选定的 GDI 对象的控件来优化绘图。 绘制所有控件之后，容器可以自动还原原始对象。）

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

本文中的示例来自 MFC ActiveX 控件向导利用默认设置创建的控件。 有关使用 MFC ActiveX 控制向导创建骨架控制应用程序的详细信息，请参阅文章[MFC ActiveX 控制向导](../mfc/reference/mfc-activex-control-wizard.md)。

所涉及的主题如下：

- [绘制由 ActiveX 控件向导创建的控件和代码以支持绘制的整个过程](#_core_the_painting_process_of_an_activex_control)

- [如何优化绘制进程](#_core_optimizing_your_paint_code)

- [如何使用图元文件绘制控件](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>ActiveX 控件的绘制过程

在最初显示或重新绘制 ActiveX 控件时，它们遵循与其他使用 MFC 开发的应用程序一样的绘制过程，但有一个重要区别：ActiveX 控件可以处于活动或非活动状态。

活动控件在 ActiveX 控件容器中通过一个子窗口表示。 与其他窗口一样，它负责在收到WM_PAINT消息时绘制自己。 控件的基类[COleControl](../mfc/reference/colecontrol-class.md)在其`OnPaint`函数中处理此消息。 此默认实现调用您的控件的 `OnDraw` 函数。

非活动控件绘制方式有所不同。 当控件处于不活动状态时，其窗口也是不可见或不存在的，因此它无法接收绘制消息。 相反，控件容器将直接调用控件的 `OnDraw` 函数。 这与活动控件的绘图过程的不同之处在于：绝不调用 `OnPaint` 成员函数。

如上面几段中所述，ActiveX 控件的更新方式取决于控件的状态。 但是，由于在这两种情况下，框架都会调用 `OnDraw` 成员函数，因此你需要在此成员函数中添加你自己的大部分绘制代码。

`OnDraw` 成员函数处理控件绘制。 当控件处于不活动状态时，控件容器调用 `OnDraw`，并传递控件容器的设备上下文以及控件占用的矩形区域的坐标。

框架传递给 `OnDraw` 成员函数的矩形包含控件占用的区域。 如果控件处于活动状态，则左上角的坐标为 (0，0)，且传递的设备上下文是针对包含控件的子窗口的。 如果控件处于不活动状态，则左上角的坐标不一定为 (0，0)，且传递的设备上下文是针对包含控件的控件容器的。

> [!NOTE]
> 重要的是，修改`OnDraw`不应依赖于矩形的左上角等于 （0， 0），并且只在传递给`OnDraw`的矩形内绘制。 如果绘制超出了矩形的区域，则会发生意外结果。

MFC ActiveX 控件向导在控件实现文件 (.CPP) 中提供的默认实现（如下所示）使用白色画笔绘制矩形，并使用当前背景色填充椭圆。

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> 绘制控件时，不应对作为*pdc*参数传递给`OnDraw`函数的设备上下文的状态进行假设。 有时，设备上下文由容器应用程序提供，不一定需要初始化为默认状态。 具体而言就是明确选择绘制代码依赖的钢笔、画笔、颜色、字体以及其他资源。

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>优化您的油漆代码

成功绘制控件自身之后的下一步是优化 `OnDraw` 函数。

ActiveX 控件绘制的默认实现将绘制整个控件区域。 这对于简单控件已经足够，但在很多情况下，如果只重新绘制需要更新的部分而非整个控件，则重新绘制控件会更快。

该`OnDraw`函数提供了一种简单的优化方法，通过传递需要重绘的控件的矩形区域*rcInvalid。* 使用这个通常小于整个控件区域的区域来加速绘制过程。

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>使用元文件绘制控件

在大多数情况下，函数的`OnDraw` *pdc*参数指向屏幕设备上下文 （DC）。 但是，在打印控件图像期间或在打印预览会话期间，接收的用于渲染的 DC 是称为“图元文件 DC”的特殊类型。 与立即处理发送给它的请求的屏幕 DC不同，图元文件 DC 会存储请求以在稍后处理。 在设计模式中，一些容器应用程序还可能选择使用图元文件 DC 渲染控件图像。

元文件绘图请求可以通过两个接口函数进行：（`IViewObject::Draw`对于非元文件绘图也可以调用此函数）和`IDataObject::GetData`。 当元文件 DC 作为参数之一传递时，MFC 框架将调用[COleControl：：OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile)。 由于这是一个虚拟成员函数，因此请在控件类中重写此函数以执行任何特殊处理。 默认行为将调用 `COleControl::OnDraw`。

若要确保能在屏幕和图元文件设备上下文中绘制控件，则必须仅使用在屏幕 DC 和图元文件 DC 中均支持的成员函数。 请注意，坐标系不能以像素为单位测量。

因为 `OnDrawMetafile` 的默认实现将调用控件的 `OnDraw` 函数，所以应仅使用同时适用于图元文件和屏幕设备上下文的成员函数，除非重写 `OnDrawMetafile`。 下面列出了可以同时在图元文件和屏幕设备上下文中使用的 `CDC` 成员函数的子集。 有关这些函数的详细信息，请参阅*MFC 参考*中的类[CDC。](../mfc/reference/cdc-class.md)

|Arc|BibBlt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

除了 `CDC` 成员函数之外，还有一些在图元文件 DC 中兼容的其他函数。 其中包括[CPalette：：AnimatePalette，CFont：：create](../mfc/reference/cpalette-class.md#animatepalette)[间接](../mfc/reference/cfont-class.md#createfontindirect)，`CBrush`以及以下三个成员函数：[创建Brush间接](../mfc/reference/cbrush-class.md#createbrushindirect)、[创建DIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush)和[创建模式画笔](../mfc/reference/cbrush-class.md#createpatternbrush)。

未记录在元文件中的函数有：[绘制焦点重新完成](../mfc/reference/cdc-class.md#drawfocusrect)、[绘制图标](../mfc/reference/cdc-class.md#drawicon)、[绘制文本](../mfc/reference/cdc-class.md#drawtext)、[排除更新、](../mfc/reference/cdc-class.md#excludeupdatergn)[填充重新执行](../mfc/reference/cdc-class.md#fillrect)、[帧重新执行](../mfc/reference/cdc-class.md#framerect)、[灰弦](../mfc/reference/cdc-class.md#graystring)、[反转、](../mfc/reference/cdc-class.md#invertrect)[滚动 DC](../mfc/reference/cdc-class.md#scrolldc)和[TabbedTextOut。](../mfc/reference/cdc-class.md#tabbedtextout) 由于图元文件 DC 实际上与设备无关，因此您不能将 SetDIBits、GetDIBits 和 CreateDIBitmap 用于图元文件 DC。 您可以将 SetDIBitsToDevice 和 StretchDIBits 与用作目标的图元文件 DC 一起使用。 [创建兼容DC，](../mfc/reference/cdc-class.md#createcompatibledc)[创建兼容的位图](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)，[和创建可丢弃的位图](../mfc/reference/cbitmap-class.md#creatediscardablebitmap)对元文件DC没有意义。

在使用图元文件 DC 时要考虑的另一点是坐标系不能以像素为单位测量。 因此，应调整所有绘图代码以适合传递到`OnDraw` *rcBounds*参数中的矩形。 这可以防止在控件之外进行意外绘制，因为*rcBounds*表示控件窗口的大小。

在实现了控件的图元文件渲染之后，请使用测试容器测试图元文件。 请参阅 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

#### <a name="to-test-the-controls-metafile-using-test-container"></a>使用测试容器测试控件的图元文件

1. 在测试**容器的编辑菜单上**，单击 **"插入新控件**"。

1. 在"**插入新控制"** 框中，选择控件并单击 **"确定**"。

   控件将显示在测试容器中。

1. 在 **"控制"** 菜单上，单击 **"绘制元文件**"。

   将出现一个单独的用于显示图元文件的窗口。 您可以更改此窗口的大小，以查看缩放会如何影响控件的图元文件。 您可以随时关闭此窗口。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
