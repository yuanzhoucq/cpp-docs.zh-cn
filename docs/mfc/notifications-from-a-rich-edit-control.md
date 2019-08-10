---
title: 来自 Rich Edit 控件的通知
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: bc4c027ff26df89539b22c6d04f1d1dc95fc459a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916402"
---
# <a name="notifications-from-a-rich-edit-control"></a>来自 Rich Edit 控件的通知

通知消息报告影响 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 的事件。 它们可以通过父窗口处理, 也可以通过使用消息反射来处理。 Rich edit 控件支持用于编辑控件以及多个其他通知消息。 可以通过设置 "事件掩码" 来确定富格编辑控件发送其父窗口的通知消息。

若要为超文本编辑控件设置事件掩码, 请使用[SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask)成员函数。 您可以使用[GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask)成员函数检索 rich edit 控件的当前事件掩码。

以下段落列出了几个具体的通知及其用法:

- EN_MSGFILTER 处理 EN_MSGFILTER 通知后, 类 (rich edit 控件或其父窗口) 可以筛选控件的所有键盘和鼠标输入。 处理程序可以通过修改指定的[MSGFILTER](/windows/desktop/api/richedit/ns-richedit-msgfilter)结构来阻止对键盘或鼠标消息进行处理, 也可以更改该消息。

- EN_PROTECTED 处理 EN_PROTECTED 通知消息, 以便在用户尝试修改受保护的文本时进行检测。 若要将某个范围内的文本标记为受保护, 可以设置受保护的字符效果。 有关详细信息, 请参阅[Rich Edit 控件中的字符格式设置](../mfc/character-formatting-in-rich-edit-controls.md)。

- EN_DROPFILES 可以通过处理 EN_DROPFILES 通知消息, 使用户能够在 rich edit 控件中删除文件。 指定的[ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-endropfiles)结构包含有关要删除的文件的信息。

- EN_SELCHANGE 应用程序可以通过处理 EN_SELCHANGE 通知消息来检测当前选定内容的更改时间。 通知消息指定包含有关新选择的信息的[SELCHANGE](/windows/desktop/api/richedit/ns-richedit-selchange)结构。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
