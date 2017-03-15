---
title: "来自 Rich Edit 控件的通知 | Microsoft Docs"
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
  - "CRichEditCtrl 类, 通知"
  - "消息, 通知"
  - "通知, 从 CRichEditCtrl"
  - "Rich Edit 控件, 通知"
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 来自 Rich Edit 控件的通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通知消息报告影响丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的事件。  使用反射，因此可以处理消息由父窗口，或，通过丰富的编辑控件。  Rich Edit 控件支持所有通知消息与编辑控件以及若干其他部分。  可以确定一条通知消息丰富的编辑控件通过设置其“事件蒙板发送其父窗口”。  
  
 若要设置丰富的编辑控件的事件蒙板，请使用 [SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md) 成员函数。  使用 [GetEventMask](../Topic/CRichEditCtrl::GetEventMask.md) 成员函数，则可以检索丰富的编辑控件的时事掩码。  
  
 以下段落列出若干特定通知及其用法：  
  
-   通知处理 **EN\_MSGFILTER** 的**EN\_MSGFILTER** 允许类，或 Rich Edit 控件或其父窗口，筛选所有键盘和鼠标输入到控件。  处理程序会阻止处理键盘或鼠标消息也可以通过修改 [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) 指定的结构更改消息。  
  
-   **EN\_PROTECTED** 句柄。检测用户何时的 **EN\_PROTECTED** 通知消息尝试修改受保护的文本。  若要标记文本范围。保护，可以将保护的字符。  有关更多信息，请参见 [Rich Edit 控件的字符格式。](../mfc/character-formatting-in-rich-edit-controls.md)。  
  
-   **EN\_DROPFILES** 您可以使用户通过处理 **EN\_DROPFILES** 通知消息将为 Rich Edit 控件的文件。  [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) 指定的结构包含有关删除的文件的信息。  
  
-   **EN\_SELCHANGE** 应用程序可以检测当前选择何时通过处理 **EN\_SELCHANGE** 通知消息更改。  通知消息指定包含有关新选择 [SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb787952) 结构的信息。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)