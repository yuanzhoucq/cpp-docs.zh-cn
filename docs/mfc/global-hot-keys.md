---
title: 全局热键
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508570"
---
# <a name="global-hot-keys"></a>全局热键

全局热键与特定 nonchild 窗口相关联。 它允许用户从系统的任何部分激活窗口。 应用程序通过将[WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey)消息发送到该窗口来设置特定窗口的全局热键。 例如, 如果`m_HotKeyCtrl`是[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)对象, 并且`pMainWnd`是一个指向在按下热键时要激活的窗口的指针, 则可以使用以下代码将控件中指定的热键与指向的窗口相关联`pMainWnd`。

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

每当用户按全局热键时, 指定的窗口就会收到一条[WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand)消息, 该消息将**SC_HOTKEY**指定为命令的类型。 此消息还会激活接收它的窗口。 由于此消息不包括任何按下的确切密钥的信息, 因此使用此方法不允许区分可能附加到同一个窗口的不同热键。 热键始终有效, 直到发送的**WM_SETHOTKEY**的应用程序退出。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
