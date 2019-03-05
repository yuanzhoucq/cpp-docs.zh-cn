---
title: 处理工具提示通知
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 079dc26fdd355c5b5e3f89f28219902e5fd74a79
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268819"
---
# <a name="handling-tool-tip-notifications"></a>处理工具提示通知

当指定**TBSTYLE_TOOLTIPS**样式，工具栏用于创建和管理工具提示控件。 工具提示是文本的一个小型的弹出窗口，其中包含描述工具栏按钮行。 隐藏的工具提示，使其不显示仅当用户将光标放在工具栏按钮和停留约半秒钟。 在光标附近显示的工具提示。

显示工具提示之前， **TTN_NEEDTEXT**通知消息发送到工具栏的所有者窗口，以检索按钮的描述性文本。 如果工具栏的所有者窗口处于`CFrameWnd`窗口中，工具提示显示而无需任何额外工作，因为`CFrameWnd`已提供默认处理程序**TTN_NEEDTEXT**通知。 如果工具栏的所有者窗口不派生自`CFrameWnd`，如对话框框中或窗体视图，您必须将条目添加到所有者窗口的消息映射，并提供消息映射中的通知处理程序。 在所有者窗口消息映射到条目如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>备注

*memberFxn*<br/>
文本所需的此按钮时要调用的成员函数。

请注意，工具提示的 id 始终为 0。

除了**TTN_NEEDTEXT**通知时，工具提示控件可以发送以下通知，向 toolbar 控件：

|通知|含义|
|------------------|-------------|
|**TTN_NEEDTEXTA**|工具提示控件需要 ASCII 文本 (仅适用于 Windows 95)|
|**TTN_NEEDTEXTW**|工具提示控件需要 UNICODE 文本 (仅适用于 Windows NT)|
|**TBN_HOTITEMCHANGE**|指示已更改的热的 （突出显示的） 项。|
|**NM_RCLICK**|指示用户已右键单击一个按钮。|
|**TBN_DRAGOUT**|指示用户已单击按钮并拖动指针离开按钮。 它允许应用程序可以从工具栏按钮实现拖放。 时收到此通知，应用程序将开始拖放操作。|
|**TBN_DROPDOWN**|指示用户已单击了使用的按钮**TBSTYLE_DROPDOWN**样式。|
|**TBN_GETOBJECT**|指示用户将指针移到使用的按钮上**TBSTYLE_DROPPABLE**样式。|

一个示例处理程序函数和有关启用工具提示的详细信息，请参阅[工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
