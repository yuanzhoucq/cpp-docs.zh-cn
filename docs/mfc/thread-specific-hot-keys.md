---
title: 线程特定的热键
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: a54aa878b0160132157879127f8335c951e91785
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290984"
---
# <a name="thread-specific-hot-keys"></a>线程特定的热键

应用程序设置特定于线程的热键 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 通过使用 Windows`RegisterHotKey`函数。 当用户按特定于线程的热键时，Windows 将发布[WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey)到特定线程的消息队列的开头的消息。 WM_HOTKEY 消息包含虚拟键代码、 位移状态和用户定义的按下了特定的热键的 ID。 标准虚拟键代码的列表，请参见 Winuser.h。 此方法的详细信息，请参阅[RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)。

请注意，位移状态标志对调用中使用`RegisterHotKey`不是返回的相同[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成员函数; 您必须转换之前，调用这些标志`RegisterHotKey`。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
