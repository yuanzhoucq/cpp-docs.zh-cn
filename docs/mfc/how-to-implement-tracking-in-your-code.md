---
title: 如何：在代码中实现跟踪
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 3d71543261021c7e20041d317401b7b7b8d0616e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621659"
---
# <a name="how-to-implement-tracking-in-your-code"></a>如何：在代码中实现跟踪

若要跟踪 OLE 项，必须处理与该项相关的某些事件，如单击项或更新文档的视图。 在所有情况下，都足以声明一个临时的[CRectTracker](reference/crecttracker-class.md)对象并通过此对象来处理该项。

当用户选择某一项或通过菜单命令插入对象时，必须使用适当的样式初始化跟踪器，以表示该 OLE 项的状态。 下表概述了 OCLIENT 示例使用的约定。 有关这些样式的详细信息，请参阅 `CRectTracker` 。

### <a name="container-styles-and-states-of-the-ole-item"></a>OLE 项的容器样式和状态

|显示样式|OLE 项的状态|
|---------------------|-----------------------|
|虚线边框|项目已链接|
|实线边框|项目已嵌入到文档中|
|重设句柄大小|当前选定项|
|阴影线边框|项目当前处于就地活动状态|
|阴影模式覆盖项|项的服务器已打开|

您可以使用检查 OLE 项的状态并设置适当样式的过程，轻松处理此初始化。 在 `SetupTracker` OCLIENT 示例中找到的函数演示跟踪器初始化。 此函数的参数是跟踪器的地址*pTracker*;指向与跟踪器相关的客户端项的指针， *pItem*;指向*pTrueRect*的指针。 有关此函数的更完整示例，请参阅 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)。

**SetupTracker**代码示例演示了一个函数;函数的行与函数功能的讨论有关：

[!code-cpp[NVC_MFCOClient#1](codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

通过设置最小大小并清除跟踪器样式来初始化跟踪器。

[!code-cpp[NVC_MFCOClient#2](codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

以下各行用于检查当前是否选中了该项以及该项是链接到文档还是嵌入到文档中。 位于边框内部的调整大小控点将添加到样式中，指示当前已选定该项。 如果项已链接到您的文档，则使用点线边框样式。 如果嵌入项，则使用实线边框。

[!code-cpp[NVC_MFCOClient#3](codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

如果项当前打开，以下代码将用阴影模式覆盖该项。

[!code-cpp[NVC_MFCOClient#4](codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

然后，只要必须显示跟踪器，就可以调用此函数。 例如，从视图类的函数中调用此函数 `OnDraw` 。 这会在每次重新绘制视图时更新跟踪器的外观。 有关完整示例，请参阅 `CMainView::OnDraw` MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)的函数。

在应用程序中，会发生需要跟踪程序代码的事件，例如调整大小、移动或检测检测。 这些操作通常指示尝试获取或移动该项。 在这种情况下，需要确定所抓取的内容：调整大小控点或调整大小控点之间的部分边框。 `OnLButtonDown`消息处理程序是测试鼠标相对于项的位置的好地方。 调用 `CRectTracker::HitTest` 。 如果测试返回了其他内容 `CRectTracker::hitOutside` ，则会调整项的大小或移动该项。 因此，应调用 `Track` 成员函数。 `CMainView::OnLButtonDown`有关完整示例，请参阅 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)中的函数。

`CRectTracker`类提供多个不同的光标形状，用于指示是否正在进行移动、调整大小或拖动操作。 若要处理此事件，请检查当前是否选中了鼠标下的项。 如果是，请调用 `CRectTracker::SetCursor` ，或调用默认处理程序。 下面的示例来自 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)：

[!code-cpp[NVC_MFCOClient#5](codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>另请参阅

[跟踪器：在您的 OLE 应用程序内实现跟踪器](trackers-implementing-trackers-in-your-ole-application.md)
