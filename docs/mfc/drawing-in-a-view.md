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
ms.openlocfilehash: 227c4614bad42706893301c69882c3f40af12e2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214339"
---
# <a name="drawing-in-a-view"></a>在视图中绘制

应用程序中的几乎所有绘图都出现在视图的 `OnDraw` 成员函数中，必须在视图类中进行重写。 （例外情况是鼠标绘图，在[通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)中进行了讨论。）你的 `OnDraw` 重写：

1. 通过调用你提供的文档成员函数来获取数据。

1. 通过调用框架传递给 `OnDraw`的设备上下文对象的成员函数来显示数据。

如果文档的数据以某种方式发生更改，则必须重新绘制视图以反映所做的更改。 通常，当用户通过文档中的视图进行更改时，会发生这种情况。 在这种情况下，视图将调用文档的[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成员函数，以通知同一文档上的所有视图自行更新。 `UpdateAllViews` 调用每个视图的[OnUpdate](../mfc/reference/cview-class.md#onupdate)成员函数。 `OnUpdate` 的默认实现将使视图的整个工作区失效。 您可以将其重写为仅使那些映射到文档的已修改部分的工作区区域无效。

类 `CDocument` 的 `UpdateAllViews` 成员函数和类 `CView` 的 `OnUpdate` 成员函数使你可以传递描述文档中修改的部分内容的信息。 此 "提示" 机制使您可以限制视图必须重绘的区域。 `OnUpdate` 采用两个 "提示" 参数。 第一种类型为**LPARAM**的*lHint*，可传递所需的任何数据，而第二种*pHint*是 `CObject`* 类型，它允许向派生自 `CObject`的任何对象传递指针。

当视图变为无效时，Windows 会向其发送**WM_PAINT**消息。 视图的[OnPaint](../mfc/reference/cwnd-class.md#onpaint)处理程序函数通过创建类[CPaintDC](../mfc/reference/cpaintdc-class.md)的设备上下文对象来响应消息，并调用视图的 `OnDraw` 成员函数。 通常不需要编写重写 `OnPaint` 处理程序函数。

"[设备上下文](../mfc/device-contexts.md)" 是一种 Windows 数据结构，其中包含有关设备（例如显示器或打印机）的绘图属性的信息。 所有绘图调用都通过设备上下文对象进行。 对于在屏幕上绘制，`OnDraw` 传递 `CPaintDC` 对象。 对于在打印机上绘图，为当前打印机传递了一个[CDC](../mfc/reference/cdc-class.md)对象集。

视图中用于绘制的代码首先检索指向文档的指针，然后通过设备上下文进行绘图调用。 以下简单的 `OnDraw` 示例说明了该过程：

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

在此示例中，您将 `GetData` 函数定义为您的派生文档类的成员。

该示例将从文档中获取的任何字符串（在视图中居中）打印。 如果 `OnDraw` 调用用于屏幕绘制，则在*pDC*中传递的 `CDC` 对象是其构造函数已调用 `BeginPaint`的 `CPaintDC`。 通过设备上下文指针对绘制函数进行调用。 有关设备上下文和绘图调用的信息，请参阅*MFC 参考*中的[CDC](../mfc/reference/cdc-class.md)类和使用[窗口对象](../mfc/working-with-window-objects.md)。

有关如何编写 `OnDraw`的更多示例，请参阅[MFC 示例](../overview/visual-cpp-samples.md#mfc-samples)。

## <a name="see-also"></a>另请参阅

[使用视图](../mfc/using-views.md)
