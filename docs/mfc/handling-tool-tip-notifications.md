---
title: 处理工具提示通知
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 41e3dbfc2269f5fbf3c12dc00c19f8a2253fd16a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626444"
---
# <a name="handling-tool-tip-notifications"></a>处理工具提示通知

指定**TBSTYLE_TOOLTIPS**样式后，工具栏会创建并管理工具提示控件。 工具提示是一个小型弹出窗口，其中包含一条描述工具栏按钮的文本。 工具提示是隐藏的，仅当用户将光标放在工具栏按钮上并在该按钮上停留大约一半秒时才会出现。 工具提示显示在光标附近。

在显示工具提示之前，会将**TTN_NEEDTEXT**通知消息发送到工具栏的所有者窗口，以检索该按钮的描述性文本。 如果工具栏的 "所有者" 窗口是一个 `CFrameWnd` 窗口，将显示工具提示而不做任何额外的工作，因为 `CFrameWnd` 有**TTN_NEEDTEXT**通知的默认处理程序。 如果工具栏的 "所有者" 窗口不是从派生的 `CFrameWnd` ，例如对话框或窗体视图，则必须将条目添加到所有者窗口的消息映射，并在消息映射中提供通知处理程序。 所有者窗口消息映射的条目如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>备注

*memberFxn*<br/>
此按钮需要文本时调用的成员函数。

请注意，工具提示的 id 始终为0。

除了**TTN_NEEDTEXT**通知外，工具提示控件还可以将以下通知发送到 toolbar 控件：

|通知|含义|
|------------------|-------------|
|**TTN_NEEDTEXTA**|工具提示控件需要 ASCII 文本（仅适用于 Windows 95）|
|**TTN_NEEDTEXTW**|工具提示控件需要 UNICODE 文本（仅适用于 Windows NT）|
|**TBN_HOTITEMCHANGE**|指示热（突出显示）项已更改。|
|**NM_RCLICK**|指示用户已右键单击某个按钮。|
|**TBN_DRAGOUT**|指示用户单击了该按钮，并将指针拖出了该按钮。 它允许应用程序从工具栏按钮实现拖放。 收到此通知时，应用程序将开始拖放操作。|
|**TBN_DROPDOWN**|指示用户已单击使用**TBSTYLE_DROPDOWN**样式的按钮。|
|**TBN_GETOBJECT**|指示用户将指针移到使用**TBSTYLE_DROPPABLE**样式的按钮上方。|

有关示例处理程序函数的详细信息和有关启用工具提示的详细信息，请参阅[工具提示](tool-tips-in-windows-not-derived-from-cframewnd.md)。

## <a name="see-also"></a>另请参阅

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控件](controls-mfc.md)
