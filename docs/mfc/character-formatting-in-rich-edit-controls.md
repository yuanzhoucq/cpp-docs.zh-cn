---
title: "Rich Edit 控件中的字符格式设置 | Microsoft Docs"
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
  - "CRichEditCtrl 类, 字符格式设置"
  - "格式设置 [C++], 字符"
  - "Rich Edit 控件, 字符格式设置"
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Rich Edit 控件中的字符格式设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的成员函数为格式化符号以及如何检索格式化信息。  对于字符，可以指定字样、大小、颜色和效果 \(粗体，则为斜体，并保护。  
  
 使用 [SetSelectionCharFormat](../Topic/CRichEditCtrl::SetSelectionCharFormat.md)[SetWordCharFormat](../Topic/CRichEditCtrl::SetWordCharFormat.md) 成员和函数，可以将字符格式。  若要确定当前选择的文本字符格式，请使用 [GetSelectionCharFormat](../Topic/CRichEditCtrl::GetSelectionCharFormat.md) 成员函数。  [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) 结构来提供这些成员函数中指定字符特性。  某一 **CHARFORMAT** 的重要成员是 **dwMask**。  在 `SetSelectionCharFormat` 和 **dwMask**`SetWordCharFormat`，指定哪些字符特性将由该函数调用设置。  `GetSelectionCharFormat` 报告第一个字符；选定的特性。**dwMask** 指定的一致。选择中的特性。  
  
 还可以获取和设置“格式”，是默认字符格式应用于后续插入的字符。  例如，应用程序，则将默认字符格式设置为粗体，并随后用户键入字符，该字符变为粗体。  若要获取和设置默认字符格式，请使用 [GetDefaultCharFormat](../Topic/CRichEditCtrl::GetDefaultCharFormat.md)[SetDefaultCharFormat](../Topic/CRichEditCtrl::SetDefaultCharFormat.md) 和成员函数。  
  
 “受保护的”字符特性不更改文本的外观。  如果用户尝试修改保护文本，丰富的编辑控件发送其父窗口的 **EN\_PROTECTED** 通知消息，允许父窗口允许或阻止更改。  使用 [SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md) 成员函数，接收此通知消息，则必须启用它。  有关 Mask 事件的更多信息，请参见 [通过丰富的编辑控件的通知](../mfc/notifications-from-a-rich-edit-control.md)，本主题后面。  
  
 前景是字符特性，但背景色是丰富的编辑控件的属性。  若要设置背景色，请使用 [SetBackgroundColor](../Topic/CRichEditCtrl::SetBackgroundColor.md) 成员函数。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)