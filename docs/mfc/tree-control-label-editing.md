---
title: "树控件标签编辑 | Microsoft Docs"
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
  - "CTreeCtrl 类, 编辑标签 "
  - "编辑树控件标签"
  - "CTreeCtrl 类中的标签编辑"
  - "树控件, 标签编辑"
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件标签编辑
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用户可以直接编辑项标签具有 **TVS\_EDITLABELS** 样式的树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\)。  用户开始编辑。单击具有焦点项的标签。  使用 [EditLabel](../Topic/CTreeCtrl::EditLabel.md) 成员函数，应用程序将开始编辑。  树控件发送编辑通知，当开始时，并且，当取消或完成时。  当编辑完成时，您应负责更新项的标签，因此，如果合适。  
  
 当编辑标签开始时，树控件发送通知消息。[TVN\_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) 通过处理此通知，您可能允许编辑某些标签并防止其他编辑。  返回 0 允许编辑，并且，返回非零防止它。  
  
 当编辑标签取消或完成时，树控件发送通知消息。[TVN\_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) `lParam` 参数为 [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) 结构的地址。  **项** 成员是一项并包括编辑文本的结构。[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) 可能您负责更新项的标签，因此，如果适当，在验证编辑的字符串之后。  如果已取消编辑，`TV_ITEM` 的 **pszText** 成员为 0。  
  
 在标签期间编辑，通常是为了响应 [TVN\_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) 通知消息，可以编辑控件用于编辑标签使用 [GetEditControl](../Topic/CTreeCtrl::GetEditControl.md) 成员函数的指针。  可以调用控件编辑的 [SetLimitText](../Topic/CEdit::SetLimitText.md) 成员函数会限制用户可以进入或子类截获和丢弃无效字符的编辑控件的文本量。  但是，请注意，将编辑控件显示，在发送*after* **TVN\_BEGINLABELEDIT** 之后。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)