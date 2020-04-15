---
title: 从公共控件接收通知
ms.date: 11/04/2016
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
ms.openlocfilehash: 9205facb5ec4e2491308020d9667a27ab8deb96b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371785"
---
# <a name="receiving-notification-from-common-controls"></a>从公共控件接收通知

公共控件是一系列子窗口，当控件中发生事件（如来自用户的输入）时，它们会将通知消息发送到父窗口。

应用程序依靠这些通知消息来确定用户希望它执行的操作。 大多数公共控件将通知消息作为 WM_NOTIFY 消息发送。 Windows 控件将大多数通知消息作为WM_COMMAND 消息发送。 [CWnd：onNotify](../mfc/reference/cwnd-class.md#onnotify)是WM_NOTIFY消息的处理程序。 与 `CWnd::OnCommand` 相同，`OnNotify` 的实现会将通知消息调度到 `OnCmdMsg` 以在消息映射中进行处理。 处理通知的消息映射条目ON_NOTIFY。 有关详细信息，请参阅[技术说明 61：ON_NOTIFY和WM_NOTIFY消息](../mfc/tn061-on-notify-and-wm-notify-messages.md)。

或者，派生类也可以使用“消息反射”处理其自己的通知消息。 有关详细信息，请参阅[技术说明 62：Windows 控件的消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)。

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>在通知消息中检索位置光标

有时，在公共控件收到某些通知消息时确定光标的当前位置很有用。 例如，当公共控件收到 NM_RCLICK 通知消息时，确定当前光标位置很有用。

达到此目的的一个简单方法是调用 `CWnd::GetCurrentMessage`。 但是，此方法仅在消息发送时检索光标位置。 由于游标可能是自发送消息以来移动的，因此必须调用`CWnd::GetCursorPos`以获取当前游标位置。

> [!NOTE]
> 只应在消息处理程序中调用 `CWnd::GetCurrentMessage`。

将以下代码添加到消息通知处理程序的主体（本例中为 NM_RCLICK）：

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

此时，鼠标光标位置存储在 `cursorPos` 对象中。

## <a name="see-also"></a>另请参阅

[制作和使用控件](../mfc/making-and-using-controls.md)<br/>
[控件](../mfc/controls-mfc.md)
