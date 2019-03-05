---
title: 来自 Rich Edit 控件的通知
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: fcb1dda1d915dc13e01effed9ba99070b825a15e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274526"
---
# <a name="notifications-from-a-rich-edit-control"></a>来自 Rich Edit 控件的通知

通知消息报告事件影响 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 它们可以处理由父窗口或者，可使用消息反射通过丰富的编辑控件本身的方法。 Rich edit 控件支持的所有使用与编辑控件，以及几个附加的通知消息。 您可以确定哪些通知消息格式文本编辑控件将发送其父窗口设置其"事件掩码"。

若要设置事件掩码 rich edit 控件，请使用[SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask)成员函数。 Rich edit 控件使用，可以检索当前事件掩码[GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask)成员函数。

以下各段列出几个特定的通知和它们的用途：

- EN_MSGFILTER 处理 EN_MSGFILTER 通知允许一个类，或者格式文本编辑控件或其父窗口中，筛选所有键盘和鼠标输入到控件。 处理程序可以防止键盘或鼠标消息正在处理或可以通过修改指定更改消息[MSGFILTER](/windows/desktop/api/richedit/ns-richedit-_msgfilter)结构。

- EN_PROTECTED 处理 EN_PROTECTED 通知消息来检测在用户尝试修改受保护的文本。 若要将范围内的文本标记为受保护，可以设置受保护的字符的效果。 有关详细信息，请参阅[Rich Edit 控件中的字符格式](../mfc/character-formatting-in-rich-edit-controls.md)。

- EN_DROPFILES 你可以让用户通过将删除 rich edit 控件中的文件处理 EN_DROPFILES 通知消息。 指定[ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-_endropfiles)结构包含有关要删除的文件的信息。

- 当前所选内容更改通过处理 EN_SELCHANGE 通知消息时，可以检测到 EN_SELCHANGE 应用程序。 通知消息指定[SELCHANGE](/windows/desktop/api/richedit/ns-richedit-_selchange)结构，它包含有关新选择信息。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
