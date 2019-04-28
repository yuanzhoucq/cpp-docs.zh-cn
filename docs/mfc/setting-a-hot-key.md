---
title: 设置热键
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a77aad4881acd04c6dabb6dce90acc01be2cfbc8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307778"
---
# <a name="setting-a-hot-key"></a>设置热键

你的应用程序可以使用提供的热键的信息 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有两种控件：

- 设置用于通过发送激活非子窗口的全局热键[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)到窗口的消息激活。

- 通过调用 Windows 函数来设置特定于线程的热键[RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
