---
title: "Rich Edit 控件中的当前选定内容 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl 类, 当前选定内容"
  - "CRichEditCtrls 中的当前选定内容"
  - "Rich Edit 控件, 当前选定内容"
  - "选择, CRichEditCtrl 中的当前选定内容"
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Rich Edit 控件中的当前选定内容
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用户可以选择中丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的文本。使用鼠标和键盘。  当前选定范围是选定的字符或插入点位置的字符均未选中。  应用程序可以获取有关当前选择的信息，将当前选择，确定当前选择发生更改并显示或隐藏选定突出显示。  
  
 若要确定在丰富的编辑控件中当前选择，请使用 [GetSel](../Topic/CRichEditCtrl::GetSel.md) 成员函数。  若要将当前选择，请使用 [SetSel](../Topic/CRichEditCtrl::SetSel.md) 成员函数。  [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) 结构来提供这些函数指定字符范围。  若要检索有关当前选择内容的信息，可以使用 [GetSelectionType](../Topic/CRichEditCtrl::GetSelectionType.md) 成员函数。  
  
 默认情况下，中，在元素获取和失去焦点时，丰富的编辑控件显示和隐藏选定突出显示。  使用 [HideSelection](../Topic/CRichEditCtrl::HideSelection.md) 成员函数，则可以随时显示或隐藏选定突出显示。  例如，应用程序可能会提供搜索"对话框查找中丰富的编辑控件的文本。  应用程序可以选择文本匹配，并且无需关闭对话框，在这种情况下，它必须使用 `HideSelection` 显示选定的情况下。  
  
 若要获取中丰富的编辑控件的选定文本，请使用 [GetSelText](../Topic/CRichEditCtrl::GetSelText.md) 成员函数。  指定的文本复制到字符数组。  必须确保数组足以容纳选定的文本以及将终止空字符。  
  
 可以为中丰富的编辑控件的字符串搜索。使用 [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) 结构对该函数指定文本范围搜索和字符串搜索的 [FindText](../Topic/CRichEditCtrl::FindText.md) 成员函数。  也可以指定这些选项。搜索是否区分大小写。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)