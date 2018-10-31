---
title: 如何：在代码中实现跟踪
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 0a6a8313c02566c4d1cde82b288b42e150651b02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428673"
---
# <a name="how-to-implement-tracking-in-your-code"></a>如何：在代码中实现跟踪

若要跟踪 OLE 项，必须处理的项，例如单击项或更新文档的视图相关的特定事件。 在所有情况下，它就足以声明临时[CRectTracker](../mfc/reference/crecttracker-class.md)对象，并通过此对象操作项。

当用户选择某个项，或将插入具有菜单命令的对象时，必须用适当的样式来表示 OLE 项的状态的跟踪器进行初始化。 下表概述了使用 OCLIENT 示例的约定。 这些样式的详细信息，请参阅`CRectTracker`。

### <a name="container-styles-and-states-of-the-ole-item"></a>容器样式和 OLE 项的状态

|显示样式|OLE 项的状态|
|---------------------|-----------------------|
|点线的边框|链接项|
|实线边框|在文档中嵌入项|
|重设句柄大小|当前未选择项|
|阴影的边框|项是当前处于就地活动状态|
|阴影图案覆盖项|项的服务器处于打开状态|

您可以处理此初始化轻松地使用检查 OLE 项的状态，并设置适当的样式的过程。 `SetupTracker`函数中的 OCLIENT 示例演示了跟踪器初始化。 此函数的参数包括跟踪器的地址*pTracker*; 以指向与跟踪程序，相关的客户端项*pItem*; 和指向一个矩形、 *pTrueRect*. 此函数的更完整示例，请参阅 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)。

**SetupTracker**代码示例显示了一个函数; 函数的行混杂在一起讨论的函数的功能：

[!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

跟踪器初始化设置的最小大小和清除跟踪器的样式。

[!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

以下代码行检查当前是否选定了项，该项是链接到文档还是嵌入其中。 调整大小图柄上边框内添加到，该值指示当前选择的项的样式。 如果该项目链接到你的文档，则使用以点分隔的边框样式。 如果嵌入项，则使用实线边框。

[!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

以下代码覆盖项用阴影图案该项当前是否打开。

[!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

然后可以调用此函数，每当时，跟踪器会显示。 例如，调用该函数从`OnDraw`视图类函数。 这会更新时重新绘制该视图跟踪器的外观。 有关完整示例，请参阅`CMainView::OnDraw`函数的 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)。

在应用程序时，会发生需要跟踪程序代码，例如调整大小、 移动或点击检测的事件。 这些操作通常表示试图进行抓取或移动项。 在这些情况下，你将需要确定抓取的内容： 重设大小句柄或之间的边界的一部分重设大小句柄。 `OnLButtonDown`消息处理程序是测试与项相关的鼠标位置的好时机。 调用`CRectTracker::HitTest`。 如果该测试返回新鲜`CRectTracker::hitOutside`，项是已调整大小或移动。 因此，应该使调用`Track`成员函数。 请参阅`CMainView::OnLButtonDown`函数位于 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)有关完整示例。

`CRectTracker`类提供了几个不同的光标形状，用于指示是否迁移后，重设大小，或拖动操作正在进行。 若要处理此事件，检查以查看是否已选择当前位于鼠标下的项。 如果是，请调用`CRectTracker::SetCursor`，或调用默认处理程序。 下面的示例是从 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>请参阅

[跟踪器：在 OLE 应用程序内实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

