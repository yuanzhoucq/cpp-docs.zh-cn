---
title: "Rich Edit 控件中的剪贴板操作 | Microsoft Docs"
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
  - "剪贴板, CRichEditCtrl 中的操作"
  - "Rich Edit 控件中的复制操作"
  - "CRichEditCtrl 类, 剪贴板操作"
  - "CRichEditCtrl 类, 粘贴操作"
  - "CRichEditCtrl 类中的剪切操作"
  - "粘贴剪贴板数据"
  - "Rich Edit 控件, 剪贴板操作"
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Rich Edit 控件中的剪贴板操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

应用程序可以粘贴剪贴板的内容读入丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) ，使用最佳的可用格式剪贴板或特定格式剪贴板。  还可以确定丰富的编辑控件是否能粘贴剪贴板格式。  
  
 使用 [复制](../Topic/CRichEditCtrl::Copy.md) 或[剪切](../Topic/CRichEditCtrl::Cut.md) 成员函数，您可以复制或剪切当前选择的内容。  同样，可以使用 [粘贴](../Topic/CRichEditCtrl::Paste.md) 成员函数，粘贴剪贴板的内容读入丰富的编辑控件。  控件粘贴它识别的第一个可用格式，假定该格式是最具描述性的格式。  
  
 若要粘贴剪贴板特定的格式，则可以使用 [PasteSpecial](../Topic/CRichEditCtrl::PasteSpecial.md) 成员函数。  此函数对应用程序粘贴特定命令（使用可以选择剪贴板格式）十分有用。  可以使用 [CanPaste](../Topic/CRichEditCtrl::CanPaste.md) 成员函数确定给定格式是否由控件识别。  
  
 还可以使用 `CanPaste` 来确定任何可用格式剪贴板是否通过丰富的编辑控件识别。  此函数在`OnInitMenuPopup` 处理程序很有用。  应用程序可能允许或使其粘贴命令变灰，这取决于控件是否能粘贴任何可用格式。  
  
 Rich Edit 控件注册两个剪贴板格式：丰富的文本格式和称为丰富编辑文本和对象的格式。  使用 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) 函数，应用程序可注册这些格式，指定 **CF\_RTF** 和 **CF\_RETEXTOBJ** 值。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)