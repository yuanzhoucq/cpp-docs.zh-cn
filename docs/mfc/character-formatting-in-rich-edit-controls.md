---
title: Rich Edit 控件中的格式设置字符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75ac8637e5157434cd5729695b30a443bbd31cf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403143"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Rich Edit 控件中的字符格式设置

可以使用格式文本编辑控件的成员函数 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 个字符的格式以及如何检索格式设置信息。 对于字符，可以指定字体、 大小、 颜色和效果如粗体、 斜体和受保护。

您可以将应用使用字符格式设置[SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat)并[SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat)成员函数。 若要确定当前字符格式设置为所选文本，请使用[GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat)成员函数。 [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat)结构使用与这些成员函数来指定字符的属性。 重要成员之一**CHARFORMAT**是**dwMask**。 在中`SetSelectionCharFormat`并`SetWordCharFormat`， **dwMask**指定字符的属性将设置此函数调用。 `GetSelectionCharFormat` 报告所选内容; 中的第一个字符的属性**dwMask**指定选择中一致的属性。

您可以还获取和设置的"默认字符格式设置，"这是应用于任何随后插入字符的格式。 例如，如果应用程序设置的默认字符格式设置为粗体，且用户随后键入一个字符，该字符为粗体。 若要获取和设置默认字符格式设置，请使用[GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat)并[SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat)成员函数。

"受保护"字符属性不会更改文本的外观。 如果用户试图修改受保护的文本，文本编辑控件将发送其父窗口**EN_PROTECTED**通知消息，从而允许父窗口，以允许或阻止该更改。 若要接收此通知消息，必须启用使用它[SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask)成员函数。 有关事件掩码的详细信息，请参阅[来自格式文本编辑控件的通知](../mfc/notifications-from-a-rich-edit-control.md)，本主题中更高版本。

前景色是一种字符属性，但背景色是 rich edit 控件的属性。 若要设置背景颜色，请使用[SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor)成员函数。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

