---
title: 线程特定的热键
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511138"
---
# <a name="thread-specific-hot-keys"></a>线程特定的热键

应用程序使用 Windows `RegisterHotKey`函数设置线程特定的热键 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md))。 当用户按线程特定的热键时, Windows 会将[WM_HOTKEY](/windows/win32/inputdev/wm-hotkey)消息发送到特定线程的消息队列的开头。 WM_HOTKEY 消息包含按下的特定热键的虚拟键代码、移位状态和用户定义的 ID。 有关标准虚拟键代码的列表, 请参阅 Winuser.h。 有关此方法的详细信息, 请参阅[RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)。

请注意, 在调用`RegisterHotKey`中使用的移位状态标志与[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成员函数返回的状态标志不同; 在调用`RegisterHotKey`之前, 必须转换这些标志。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
