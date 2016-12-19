---
title: "Rich Edit 控件概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Rich Edit 控件"
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控件概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!IMPORTANT]
>  如果在对话框使用丰富的编辑控件 \(无论应用程序是否是 SDI，MDI 或基于对话框\)，必须一次调用 [AfxInitRichEdit](../Topic/AfxInitRichEdit.md)，在显示对话框之前。  调用此函数的典型排列程序的 `InitInstance` 成员函数。  不需要调用它，仅首次调用时每次显示对话框。  如果您使用 `CRichEditView`，您不必调用 `AfxInitRichEdit`。  
  
 Rich Edit 控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 提供用于格式化文本提供编程接口。  但是，应用程序必须实现任何必需用户界面的组件具有格式设置操作用户活动。  也就是说将选定文本更改的字符或段落特性的 Rich Edit 控件支持。  特性字符的一些示例为粗体，将使用斜体、字体系列和磅值。  段落对齐特性的示例包括、Margins 和制表位。  但是，将由提供用户界面的属性，不论为工具栏按钮、菜单项或对话框格式化符号。  也具有查询当前选定方面的 Rich Edit 控件的函数。  如果选定具有粗体字符格式特性，使用这些函数显示特性的当前设置，例如，在设置 UI 命令的选中标记。  
  
 有关字符和段落格式设置的更多信息，请参见 [格式字符](../mfc/character-formatting-in-rich-edit-controls.md) 后和 [段落格式](../mfc/paragraph-formatting-in-rich-edit-controls.md) 本主题。  
  
 Rich Edit 控件支持使用的几乎任何操作并通知消息的多行编辑控件相同。  因此，已使用控件编辑的应用程序可以轻松更改使用丰富的编辑控件。  其他消息和通知启用应用程序访问功能特有 Rich Edit 控件。  有关内容控件的信息，请参见[CEdit](../mfc/reference/cedit-class.md)。  
  
 通知有关的更多信息，请参见 [通过丰富的编辑控件的通知](../mfc/notifications-from-a-rich-edit-control.md) 本主题后。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)