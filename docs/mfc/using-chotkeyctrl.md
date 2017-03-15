---
title: "使用 CHotKeyCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CHotKeyCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHotKeyCtrl 类, using"
  - "热键控件"
  - "键, 热键和 CHotKeyCtrl"
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用 CHotKeyCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

热键一控件，由 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)类，是查看组合键文本表示用户类型到它的一个窗口，如 CTRL\+SHIFT\+Q。  它还维护此键的内部表示形式。虚拟键代码和表示 Shift 状态的一组标志的形式。  热键控件并不实际设置热键 \- 执行这取决于程序。\(对于标准虚拟键代码列表，请参见 Winuser.h。\)  
  
 使用一热键控件使用户的输入才能哪个热键可以与 Windows 或线程。  当要求用户分配热键时，热键控件通常用对话框，如可能显示。  为程序负责从热键控件检索描述热键的值并调用适当的函数关联热键与 Windows 或线程。  
  
## 您想进一步了解什么？  
  
-   [使用热键控件](../mfc/using-a-hot-key-control.md)  
  
-   [设置热键](../mfc/setting-a-hot-key.md)  
  
-   [全局热键](../mfc/global-hot-keys.md)  
  
-   [线程特定的热键](../mfc/thread-specific-hot-keys.md)  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)