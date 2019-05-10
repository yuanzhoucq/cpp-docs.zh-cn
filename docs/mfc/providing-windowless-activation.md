---
title: 提供无窗口激活
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: 9d60c309d5644c106e6c85a0c7b3988916be7193
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386767"
---
# <a name="providing-windowless-activation"></a>提供无窗口激活

窗口创建代码 (即，一切在调用时，会发生情况`CreateWindow`) 执行成本很高。 用来维护屏幕上的窗口的控件必须管理窗口的消息。 因此，无窗口控件比有窗口控件更快。

无窗口控件的进一步好处是，与有窗口控件不同，无窗口控件支持透明绘制和非矩形屏幕区域。 透明控件的常见示例是带有透明背景的文本控件。 该控件将绘制文本，但不会绘制背景，因此文本下的任何内容都将显露出来。 更新的窗体通常使用非矩形控件，如箭头按钮和圆形按钮。

通常，控件不需要自己的窗口，相反，它可以使用其容器的窗口服务，前提是该容器已被编写为支持无窗口对象。 无窗口控件与早期的容器向后兼容。 在未编写为支持无窗口控件的早期容器中，无窗口控件将在活动时创建窗口。

由于无窗口控件没有自己的窗口，因此容器将负责提供本应由控件自己的窗口提供的服务。 例如，如果控件需要查询键盘焦点、捕获鼠标或获取设备上下文，这些操作将由容器管理。 容器将使用 `IOleInPlaceObjectWindowless` 接口将发送给其窗口的用户输入消息传送到相应的无窗口控件。 (请参阅*ActiveX SDK*有关此接口的说明。)`COleControl`成员函数将调用这些服务在容器中的。

若要让控件使用无窗口激活，包括**windowlessActivate**标志的标志返回的集中[colecontrol:: Getcontrolflags](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如：

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

如果你选择自动生成代码以包括此标志**无窗口激活**选项卡上[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX 控件向导页。

启用无窗口激活后，容器会将输入消息委托给控件的 `IOleInPlaceObjectWindowless` 接口。 在相应地调整鼠标坐标后，`COleControl` 的此接口的实现将会在控件的消息映射中调度消息。 您可以通过将对应的项添加到消息映射来处理普通窗口消息之类的消息。 在这些消息的处理程序中，避免使用*m_hWnd*成员变量 （或使用它的任何成员函数） 不首先检查其值不**NULL**。

`COleControl` 提供了根据需要从容器中调用鼠标捕获、键盘焦点、滚动和其他窗口服务的成员函数，包括：

- [GetFocus](../mfc/reference/colecontrol-class.md#getfocus)， [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture)， [SetCapture](../mfc/reference/colecontrol-class.md#setcapture)， [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc)， [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

在无窗口控件中，您应总是使用 `COleControl` 成员函数而不是对应的 `CWnd` 成员函数或其相关的 Win32 API 函数。

您可能希望无窗口控件是 OLE 拖放操作的目标。 通常，这需要将该控件的窗口注册为放置目标。 由于该控件没有自己的窗口，容器将使用自己的窗口作为放置目标。 该控件提供了 `IDropTarget` 接口的实现，容器可在适当时向其委托调用。 若要公开此接口到容器，重写[colecontrol:: Getwindowlessdroptarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget)。 例如：

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)
