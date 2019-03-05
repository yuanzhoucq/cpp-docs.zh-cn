---
title: 在视图中绘制
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: 77844ebd31f624229870d27c72b08a987b7533bd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280766"
---
# <a name="drawing-in-a-view"></a>在视图中绘制

在应用程序中几乎所有的绘图发生在视图中`OnDraw`成员函数，您必须在视图类中重写。 (例外情况是鼠标绘制中, 所述[通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)。)你`OnDraw`重写：

1. 通过调用成员函数提供的文档获取数据。

1. 通过调用成员函数的框架将传递给一个设备上下文对象中显示的数据`OnDraw`。

当以某种方式更改文档的数据时，必须重绘视图以反映所做的更改。 通常情况下，发生这种情况时用户可以通过在文档视图的更改。 在这种情况下，视图调用文档的[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成员函数，以通知自行更新同一文档上的所有视图。 `UpdateAllViews` 调用每个视图[OnUpdate](../mfc/reference/cview-class.md#onupdate)成员函数。 默认实现`OnUpdate`使该视图的整个客户端区域无效。 可以重写它要使之无效仅这些区域的工作区映射到文档的修改后的部分。

`UpdateAllViews`类的成员函数`CDocument`并`OnUpdate`类的成员函数`CView`允许传入描述文档的哪些部分已修改的信息。 此"提示"机制，可以限制该视图必须重绘的区域。 `OnUpdate` 采用两个"提示"参数。 第一种*lHint*，类型的**LPARAM**，可让您喜欢，第二个，任何数据传递*pHint*，类型的`CObject`*，允许将指针传递到派生的任何对象从`CObject`。

Windows 当视图变为无效时，将其发送**WM_PAINT**消息。 该视图的[OnPaint](../mfc/reference/cwnd-class.md#onpaint)处理程序函数将响应消息通过创建类的设备上下文对象[CPaintDC](../mfc/reference/cpaintdc-class.md) ，并调用视图的`OnDraw`成员函数。 你通常无需编写的重写`OnPaint`处理程序函数。

一个[设备上下文](../mfc/device-contexts.md)是 Windows 数据结构，其中包含有关的绘制特性的显示器或打印机等设备的信息。 所有绘图调用都是通过设备上下文对象。 在屏幕上，绘制`OnDraw`传递`CPaintDC`对象。 对于在打印机上绘制，它传递[CDC](../mfc/reference/cdc-class.md)对象为当前的打印机设置。

在视图中绘制的代码首先检索指向文档，然后进行绘图调用通过设备上下文。 以下是一个简单`OnDraw`示例阐释了过程：

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

在此示例中，将定义`GetData`函数作为派生的文档类的成员。

该示例将打印它获取从文档，以在视图中为中心的任何字符串。 如果`OnDraw`调用是针对屏幕绘制`CDC`对象中传递*pDC*是`CPaintDC`已调用其构造函数`BeginPaint`。 对绘图函数的调用通过设备上下文指针。 有关设备上下文和绘图调用的信息，请参阅类[CDC](../mfc/reference/cdc-class.md)中*MFC 参考*并[使用窗口对象](../mfc/working-with-window-objects.md)。

有关如何编写的更多示例`OnDraw`，请参阅[MFC 示例](../visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[使用视图](../mfc/using-views.md)
