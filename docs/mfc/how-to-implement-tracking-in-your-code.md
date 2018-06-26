---
title: 如何： 在代码中实现跟踪 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc21369dd8d241bd00da2a0a8005c977094c3abf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932089"
---
# <a name="how-to-implement-tracking-in-your-code"></a>如何：在代码中实现跟踪
若要跟踪的 OLE 项目，你必须处理到项，例如单击项或更新该文档的视图相关的某些事件。 在所有情况下，只需声明一个临时[CRectTracker](../mfc/reference/crecttracker-class.md)对象，并通过此对象操作项。  
  
 当用户选择某一项或插入具有菜单命令的对象时，必须初始化用适当的样式来表示 OLE 项的状态的跟踪。 下表概述了使用 OCLIENT 示例的约定。 有关这些样式的详细信息，请参阅`CRectTracker`。  
  
### <a name="container-styles-and-states-of-the-ole-item"></a>容器样式和的 OLE 项的状态  
  
|显示样式|OLE 项的状态|  
|---------------------|-----------------------|  
|虚线的边框|链接项|  
|实心边框|项嵌入到文档中|  
|重设句柄大小|当前选定项|  
|阴影的边框|项是当前处于就地活动状态|  
|阴影图案覆盖项|项的服务器处于打开状态|  
  
 你可以处理此初始化轻松地使用检查 OLE 项的状态，并设置适当的样式的过程。 `SetupTracker` OCLIENT 示例中找到的函数演示跟踪程序初始化。 此函数的参数包括跟踪器，地址*pTracker*; 指向与跟踪程序，客户端项的指针*pItem*; 以及一个矩形的指针*pTrueRect*. 此函数的更完整示例，请参阅 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)。  
  
 **SetupTracker**的代码示例展示了一个单一的函数; 函数的行混杂在一起的函数的功能的讨论：  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 通过设置的最小大小，然后清除跟踪器样式初始化跟踪器。  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 以下行检查当前是否选定了项，项是链接到文档还是嵌入。 调整大小图柄位于边框内将添加到指示当前选定项的样式。 如果该项目链接到你的文档，则使用虚线的边框样式。 如果嵌入项，则使用实线边框。  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 下面的代码覆盖用阴影图案如果该项是当前项打开。  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 然后，可以调用此函数，只要跟踪程序获得要显示。 例如，调用该函数从`OnDraw`的视图类的函数。 每当重新绘制视图时，这会更新跟踪器的外观。 有关完整示例，请参阅`CMainView::OnDraw`MFC OLE 示例函数[OCLIENT](../visual-cpp-samples.md)。  
  
 在你的应用程序，将发生了需要跟踪器代码，例如大小调整、 移动或命中检测、 事件。 这些操作通常表明试图进行抓取或移动项。 在这些情况下，你将需要确定抓取的内容： 重设大小句柄或之间的边框的一部分重设大小句柄。 `OnLButtonDown`消息处理程序是一个好的测试与项相关的鼠标位置。 调用`CRectTracker::HitTest`。 如果测试返回新鲜`CRectTracker::hitOutside`，项是正在调整大小，或移动。 因此，你应使调用`Track`成员函数。 请参阅`CMainView::OnLButtonDown`函数位于 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)有关完整示例。  
  
 `CRectTracker`类提供用于指示是否移动、 调整大小，或拖动操作正在进行的多个不同的游标形状。 若要处理此事件，请检查以查看是否选中当前下鼠标的项。 如果是，请调用`CRectTracker::SetCursor`，或调用的默认处理。 下面的示例是从 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md):  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [跟踪器：在 OLE 应用程序内实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

