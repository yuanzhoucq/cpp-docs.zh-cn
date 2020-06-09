---
title: Rich Edit 控件中的当前选定内容
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 9591f1aeb4e159b9b4f70945d6248a3b8d1dc827
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626496"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Rich Edit 控件中的当前选定内容

用户可以使用鼠标或键盘在 rich edit 控件（[CRichEditCtrl](reference/cricheditctrl-class.md)）中选择文本。 当前选定内容是所选字符的范围，或者，如果未选择任何字符，则为插入点的位置。 应用程序可以获取有关当前所选内容的信息、设置当前选定内容、确定当前所选内容的更改时间以及显示或隐藏选择突出显示。

若要确定 rich edit 控件中的当前选定内容，请使用[GetSel](reference/cricheditctrl-class.md#getsel)成员函数。 若要设置当前所选内容，请使用[SetSel](reference/cricheditctrl-class.md#setsel)成员函数。 [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)结构与这些函数结合使用，以指定一个范围内的字符。 若要检索当前所选内容的内容的相关信息，可以使用[GetSelectionType](reference/cricheditctrl-class.md#getselectiontype)成员函数。

默认情况下，富编辑控件显示并隐藏突出显示的选定内容。 您可以使用[HideSelection](reference/cricheditctrl-class.md#hideselection)成员函数随时显示或隐藏选择突出显示。 例如，应用程序可能会提供一个搜索对话框，用于在 rich edit 控件中查找文本。 应用程序可以选择匹配文本而不关闭对话框，在这种情况下，必须使用 `HideSelection` 突出显示所选内容。

若要在 rich edit 控件中获取选定的文本，请使用[GetSelText](reference/cricheditctrl-class.md#getseltext)成员函数。 文本将复制到指定的字符数组。 必须确保数组足够大，以便保存选定文本和终止 null 字符。

您可以使用[FindText](reference/cricheditctrl-class.md#findtext)成员函数在 rich edit 控件中搜索字符串。用于此函数的[FINDTEXTEX](/windows/win32/api/richedit/ns-richedit-findtextexw)结构指定要搜索的文本范围和要搜索的字符串。 你还可以指定此类选项，因为搜索是否区分大小写。

## <a name="see-also"></a>另请参阅

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控件](controls-mfc.md)
