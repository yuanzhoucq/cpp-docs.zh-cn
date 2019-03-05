---
title: Rich Edit 控件中的当前选定内容
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 4516c4506419169ac3ab284e6c59cae71595be59
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286859"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Rich Edit 控件中的当前选定内容

用户可以选择在 rich edit 控件中的文本 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 通过使用鼠标或键盘。 当前所选内容是所选字符的范围或选定的插入点，如果任何字符的位置。 应用程序可以获取有关当前所选内容的信息，设置当前选定内容，确定在当前所选内容更改，并显示或隐藏所选内容突出显示。

若要确定格式文本编辑控件中的当前所选内容，请使用[GetSel](../mfc/reference/cricheditctrl-class.md#getsel)成员函数。 若要设置当前选定内容，请使用[SetSel](../mfc/reference/cricheditctrl-class.md#setsel)成员函数。 [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)结构使用这些函数使用指定的字符范围。 若要检索当前所选内容的信息，可以使用[GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype)成员函数。

默认情况下，rich edit 控件显示和隐藏选择突出显示，当获得或失去焦点时。 您可以通过显示或隐藏选择突出显示在任何时候使用[HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection)成员函数。 例如，应用程序可能会提供搜索对话框 rich edit 控件中查找文本。 应用程序可能会选择匹配的文本而无需关闭该对话框，在这种情况下它必须使用`HideSelection`以突出显示所选内容。

若要获取 rich edit 控件中的所选的文本，请使用[GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext)成员函数。 该文本复制到指定的字符数组。 您必须确保数组足够大以保存所选的文本加上终止 null 字符。

可以使用 rich edit 控件中的字符串搜索[FindText](../mfc/reference/cricheditctrl-class.md#findtext)成员函数[FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa)结构，与此函数可指定搜索和要搜索的字符串的文本范围。 此外可以将此类选项指定为搜索是否区分大小写。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
