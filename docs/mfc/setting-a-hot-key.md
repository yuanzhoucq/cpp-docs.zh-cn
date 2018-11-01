---
title: 设置热键
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a5dc885767137a4e53d1ea0d066944d5f276c38c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508792"
---
# <a name="setting-a-hot-key"></a>设置热键

你的应用程序可以使用提供的热键的信息 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有两种控件：

- 设置用于通过发送激活非子窗口的全局热键[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)到窗口的消息激活。

- 通过调用 Windows 函数来设置特定于线程的热键[RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309)。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

