---
title: "Rich Edit 控件中的当前选定内容 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5f0d9332d1118809ae3d62c187ec848ec95ffbf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="current-selection-in-a-rich-edit-control"></a>Rich Edit 控件中的当前选定内容
用户可以选择 rich edit 控件中的文本 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 通过使用鼠标或键盘。 当前所选内容的所选的字符范围或选定的插入点，如果没有字符的位置。 应用程序可以获取有关当前所选内容的信息、 设置当前所选内容、 确定在当前选择会有所变化，以及显示或隐藏所选内容突出显示。  
  
 若要确定在 rich edit 控件中的当前所选内容，请使用[GetSel](../mfc/reference/cricheditctrl-class.md#getsel)成员函数。 若要设置当前所选内容，使用[SetSel](../mfc/reference/cricheditctrl-class.md#setsel)成员函数。 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构配合使用，这些函数可指定的字符范围。 若要检索的当前选定内容的相关信息，可以使用[GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype)成员函数。  
  
 默认情况下，rich edit 控件显示和隐藏选择突出显示，在获得或失去焦点时。 你可以通过显示或隐藏选择突出显示在任何时候使用[HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection)成员函数。 例如，应用程序可能会提供 rich edit 控件中查找文本搜索对话框。 应用程序可能选择匹配的文本，而不关闭对话框中，在这种情况下它必须使用`HideSelection`以突出显示所选内容。  
  
 若要获取 rich edit 控件中的所选的文本，请使用[GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext)成员函数。 文本复制到指定的字符数组。 你必须确保数组足够大以保存所选的文本加上终止 null 字符。  
  
 可以在多用户环境中搜索 rich edit 控件中的字符串，通过使用[FindText](../mfc/reference/cricheditctrl-class.md#findtext)成员函数[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)结构使用此函数使用指定的搜索和要搜索的字符串的文本范围。 你还可以搜索是否区分大小写指定此类选项。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

