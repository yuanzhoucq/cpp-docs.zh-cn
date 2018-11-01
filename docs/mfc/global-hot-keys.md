---
title: 全局热键
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 4cafee311f71d8165380b3fb7e192e7032b7941c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529930"
---
# <a name="global-hot-keys"></a>全局热键

全局热键是与特定的非子窗口相关联。 它允许用户激活系统的任何部分中的窗口。 应用程序通过发送在设置特定窗口的全局热键[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)给该窗口的消息。 例如，如果`m_HotKeyCtrl`是[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)对象和`pMainWnd`的指针到按下了热键时激活窗口，可以使用下面的代码，以将热键与控件中指定相关联指向窗口`pMainWnd`。

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

每当用户按全局热键，指定的窗口接收[WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand)指定的消息**SC_HOTKEY**作为命令的类型。 此消息还会激活接收它的窗口。 因为此消息不包含任何信息的键，按下，使用此方法不允许区分不同可能附加到同一个窗口的热键。 热键之前发送的应用程序将保持有效**WM_SETHOTKEY**退出。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

