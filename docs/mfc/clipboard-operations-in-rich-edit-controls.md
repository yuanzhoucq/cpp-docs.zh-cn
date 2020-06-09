---
title: Rich Edit 控件中的剪贴板操作
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: 3dea112ed32ae618991f6ff5f05823bd5be001b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624861"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Rich Edit 控件中的剪贴板操作

应用程序可以使用最佳的剪贴板格式或特定的剪贴板格式将剪贴板的内容粘贴到丰富的编辑控件（[CRichEditCtrl](reference/cricheditctrl-class.md)）中。 您还可以确定格式文本编辑控件是否能粘贴剪贴板格式。

您可以使用 "[复制](reference/cricheditctrl-class.md#copy)" 或 "[剪切](reference/cricheditctrl-class.md#cut)" 成员函数来复制或剪切当前选定内容的内容。 同样，可以使用 "[粘贴](reference/cricheditctrl-class.md#paste)成员" 函数将剪贴板的内容粘贴到丰富的编辑控件中。 该控件将粘贴它识别的第一种可用格式，该格式可能是最具描述性的格式。

若要粘贴特定剪贴板格式，可以使用[PasteSpecial](reference/cricheditctrl-class.md#pastespecial)成员函数。 此函数对使用“选择性粘贴”命令（使用户能够选择剪贴板格式）的应用程序特别有用。 可以使用[CanPaste](reference/cricheditctrl-class.md#canpaste)成员函数来确定控件是否识别给定格式。

您还可使用 `CanPaste` 确定格式文本编辑控件是否可识别任何可用剪贴板格式。 此函数在 `OnInitMenuPopup` 处理程序中很有用。 应用程序可能启用或灰显“粘贴”命令，这取决于控件能否粘贴任何可用格式。

文本格式编辑控件将注册两种剪贴板格式：RTF 格式和称为“RichEdit 文本和对象”的格式。 应用程序可以通过使用[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数来注册这些格式，同时指定**CF_RTF**和**CF_RETEXTOBJ**值。

## <a name="see-also"></a>另请参阅

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控件](controls-mfc.md)
