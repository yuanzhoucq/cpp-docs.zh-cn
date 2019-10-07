---
title: Rich Edit 控件中的字符格式设置
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 3ff9be0909a36179802e5f210e728c2bf57b1f02
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739515"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Rich Edit 控件中的字符格式设置

您可以使用 rich edit 控件（[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)）的成员函数设置字符格式，并检索格式设置信息。 对于字符，可以指定字体、大小、颜色和效果（如粗体、斜体和受保护）。

可以通过使用[SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat)和[SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat)成员函数应用字符格式设置。 若要确定所选文本的当前字符格式设置，请使用[GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat)成员函数。 [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)结构与这些成员函数结合使用，以指定字符特性。 **CHARFORMAT**的一个重要成员是**dwMask**。 在`SetSelectionCharFormat`和`SetWordCharFormat`中， **dwMask**指定此函数调用将设置哪些字符特性。 `GetSelectionCharFormat`报告所选内容中第一个字符的属性;**dwMask**指定在整个选定内容中一致的属性。

还可以获取和设置 "默认字符格式设置"，这是应用于任何后续插入字符的格式。 例如，如果应用程序将默认字符格式设置为粗体，然后用户键入一个字符，则该字符为粗体。 若要获取和设置默认字符格式设置，请使用[GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat)和[SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat)成员函数。

"Protected" 字符属性不会更改文本的外观。 如果用户尝试修改受保护的文本，则丰富的编辑控件将向其父窗口发送**EN_PROTECTED**通知消息，允许父窗口允许或阻止更改。 若要接收此通知消息，必须使用[SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask)成员函数来启用它。 有关事件掩码的详细信息，请参阅本主题后面的[从 Rich Edit 控件发出的通知](../mfc/notifications-from-a-rich-edit-control.md)。

前景颜色是字符属性，但背景色是富编辑控件的属性。 若要设置背景色，请使用[SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor)成员函数。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
