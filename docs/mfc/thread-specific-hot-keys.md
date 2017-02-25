---
title: "线程特定的热键 | Microsoft Docs"
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
  - "访问键 [C++], 热键"
  - "CHotKeyCtrl 类, 线程特定的热键"
  - "键盘快捷键 [C++], 热键"
  - "线程处理 [C++], CHotKeyCtrl 中的热键"
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 线程特定的热键
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

应用程序将一种线程特定热键 \([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)\) 使用 **RegisterHotKey** 函数，窗口。  当用户按一种线程特定热键时，Windows 将 [WM\_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) 消息到特定线程的消息队列的开头。  **WM\_HOTKEY** 消息包含会按特定热键的虚拟键代码、Shift 状态和用户定义的 ID。  有关标准虚拟键代码列表，请参见 Winuser.h。  有关该方法的更多信息，请参见 [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
 请注意用于调用移位状态标志设置为 **RegisterHotKey** 不与 [GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md) 成员函数返回的结果；必须在调用 **RegisterHotKey**前转换这些标志。  
  
## 请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)