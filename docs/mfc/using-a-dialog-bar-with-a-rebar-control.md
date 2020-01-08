---
title: 对 Rebar 控件使用对话栏
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: e4e786d3670ec74b734739e29aa7e3e33b5af384
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302362"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>对 Rebar 控件使用对话栏

如[Rebar 控件和带区](../mfc/rebar-controls-and-bands.md)中所述，每个带区只能包含一个子窗口（或控件）。 如果希望每个带区包含多个子窗口，则这可能是一项限制。 一种方便的解决方法是创建一个具有多个控件的对话框资源，然后向 rebar 控件添加一条 rebar 带区（包含对话栏）。

通常情况下，如果希望对话栏条带显示为透明，则可以为对话栏对象设置 WS_EX_TRANSPARENT 扩展样式。 但是，因为 WS_EX_TRANSPARENT 在正确地绘制对话栏的背景时有一些问题，您需要做一些额外的工作才能实现所需的效果。

下面的过程详细说明了在不使用 WS_EX_TRANSPARENT 扩展样式的情况下实现透明度所需的步骤。

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>在 rebar 带区中实现透明对话栏

1. 使用 "[添加类" 对话框](../mfc/reference/adding-an-mfc-class.md)，添加实现对话栏对象的新类（例如 `CMyDlgBar`）。

1. 为 WM_ERASEBKGND 消息添加处理程序。

1. 在新的处理程序中，修改现有代码，使其与以下示例匹配：

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. 为 WM_MOVE 消息添加处理程序。

1. 在新的处理程序中，修改现有代码，使其与以下示例匹配：

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

新的处理程序通过将 WM_ERASEBKGND 消息转发到父窗口，并在每次移动对话框对象时强制重绘来模拟对话栏的透明度。

## <a name="see-also"></a>另请参阅

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
