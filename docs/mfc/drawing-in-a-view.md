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
ms.openlocfilehash: c60d99fdebcd64ad844bc19918a30beb90b86af3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618941"
---
# <a name="drawing-in-a-view"></a>在视图中绘制

应用程序中的几乎所有绘图都出现在视图的 `OnDraw` 成员函数中，必须在视图类中进行重写。 （例外情况是鼠标绘图，在[通过视图解释用户输入](interpreting-user-input-through-a-view.md)中进行了讨论。）`OnDraw`替代：

1. 通过调用你提供的文档成员函数来获取数据。

1. 通过调用框架传递到的设备上下文对象的成员函数来显示数据 `OnDraw` 。

如果文档的数据以某种方式发生更改，则必须重新绘制视图以反映所做的更改。 通常，当用户通过文档中的视图进行更改时，会发生这种情况。 在这种情况下，视图将调用文档的[UpdateAllViews](reference/cdocument-class.md#updateallviews)成员函数，以通知同一文档上的所有视图自行更新。 `UpdateAllViews`调用每个视图的[OnUpdate](reference/cview-class.md#onupdate)成员函数。 的默认实现 `OnUpdate` 将使视图的整个工作区失效。 您可以将其重写为仅使那些映射到文档的已修改部分的工作区区域无效。

`UpdateAllViews`类的成员函数 `CDocument` 和类的 `OnUpdate` 成员函数 `CView` 使你可以传递描述文档中修改的部分内容的信息。 此 "提示" 机制使您可以限制视图必须重绘的区域。 `OnUpdate`采用两个 "提示" 参数。 第一种是类型为**LPARAM**的*lHint*，它允许传递你喜欢的任何数据，而第二个*pHint*为类型 `CObject` *，使你能够向派生自的任何对象传递指针 `CObject` 。

当视图变为无效时，Windows 会向其发送**WM_PAINT**消息。 视图的[OnPaint](reference/cwnd-class.md#onpaint)处理程序函数通过创建类[CPaintDC](reference/cpaintdc-class.md)的设备上下文对象来响应消息，并调用视图的 `OnDraw` 成员函数。 通常不需要编写重写 `OnPaint` 处理程序函数。

"[设备上下文](device-contexts.md)" 是一种 Windows 数据结构，其中包含有关设备（例如显示器或打印机）的绘图属性的信息。 所有绘图调用都通过设备上下文对象进行。 对于在屏幕上绘制， `OnDraw` 传递 `CPaintDC` 对象。 对于在打印机上绘图，为当前打印机传递了一个[CDC](reference/cdc-class.md)对象集。

视图中用于绘制的代码首先检索指向文档的指针，然后通过设备上下文进行绘图调用。 以下简单 `OnDraw` 示例演示了该过程：

[!code-cpp[NVC_MFCDocView#1](codesnippet/cpp/drawing-in-a-view_1.cpp)]

在此示例中，您可以将 `GetData` 函数定义为您的派生文档类的成员。

该示例将从文档中获取的任何字符串（在视图中居中）打印。 如果 `OnDraw` 调用用于屏幕绘制，则 `CDC` 在*pDC*中传递的对象是 `CPaintDC` 其构造函数已调用的 `BeginPaint` 。 通过设备上下文指针对绘制函数进行调用。 有关设备上下文和绘图调用的信息，请参阅*MFC 参考*中的[CDC](reference/cdc-class.md)类和使用[窗口对象](working-with-window-objects.md)。

有关如何编写的更多示例 `OnDraw` ，请参阅[MFC 示例](../overview/visual-cpp-samples.md#mfc-samples)。

## <a name="see-also"></a>另请参阅

[使用视图](using-views.md)
