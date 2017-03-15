---
title: "使用热键控件 | Microsoft Docs"
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
  - "CHotKeyCtrl 类, using"
  - "热键控件"
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用热键控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

热键一控件的典型用法遵循以下模式：  
  
-   创建控件。  如果控件在对话框模板指定的，该对话框自动创建，创建时。\(您应具有对应于这些热键控件。\) 的对话框类的 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) 一个成员或者，可以使用 [创建](../Topic/CHotKeyCtrl::Create.md) 成员函数创建控件作为一个子窗口的所有窗口。  
  
-   如果要设置控件的默认值，请调用成员函数。[SetHotKey](../Topic/CHotKeyCtrl::SetHotKey.md) 如果要禁止某些 Shift 状态，调用 [SetRules](../Topic/CHotKeyCtrl::SetRules.md)。  若要在对话框的控件，一个好时机执行在此对话框的函数 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)。  
  
-   用户与控件交互按一热组合键，则这些热键控件具有焦点时。  通过用户单击对话框的按钮。然后指示由于此任务完成的，而。  
  
-   当程序收到通知时用户选择热键，应使用 [GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md) 热键成员函数从控件检索虚拟键 Shift 和状态值。  
  
-   一旦知道密钥用户选择，您可以设置这些热键使用 [热键设置](../mfc/setting-a-hot-key.md)中介绍的方法之一。  
  
-   热键如果控件在对话框，将自动销毁它和 `CHotKeyCtrl` 对象。  否则，您需要确保正确销毁控件和 `CHotKeyCtrl` 对象。  
  
## 请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)