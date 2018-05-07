---
title: Rich Edit 控件中的格式设置字符 |Microsoft 文档
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
ms.openlocfilehash: c02165635e8715c1fcac28b9fbee72612b72c1f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="character-formatting-in-rich-edit-controls"></a>Rich Edit 控件中的字符格式设置
你可以使用 rich edit 控件的成员函数 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 字符进行格式，以及如何检索格式设置信息。 对于字符，你可以指定字体、 大小、 颜色和效果如粗体、 斜体、 和受保护。  
  
 你可以应用使用的字符格式[SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat)和[SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat)成员函数。 若要确定所选文本格式设置的当前字符，请使用[GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat)成员函数。 [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构用于这些成员函数用来指定字符的属性。 重要成员之一**CHARFORMAT**是**dwMask**。 在`SetSelectionCharFormat`和`SetWordCharFormat`， **dwMask**指定将由此函数调用设置哪些字符属性。 `GetSelectionCharFormat` 报表中所选内容; 第一个字符的属性**dwMask**指定选择中一致的属性。  
  
 你可以获取和设置"默认字符格式设置，"这是应用于任何随后插入字符的格式。 例如，如果应用程序设置的默认字符格式设置为粗体，且用户随后键入一个字符，该字符为粗体。 若要获取和设置默认字符格式设置，使用[GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat)和[SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat)成员函数。  
  
 "受保护"字符属性不会更改文本的外观。 如果用户尝试修改受保护的文本，rich edit 控件将发送其父窗口**EN_PROTECTED**通知消息，允许父窗口，以允许或阻止更改。 若要收到此通知消息，必须启用使用它[SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask)成员函数。 有关事件掩码的详细信息，请参阅[来自格式文本编辑控件的通知](../mfc/notifications-from-a-rich-edit-control.md)，本主题中更高版本。  
  
 前景色是一种字符属性，但背景色是 rich edit 控件的属性。 若要设置的背景色，使用[SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

