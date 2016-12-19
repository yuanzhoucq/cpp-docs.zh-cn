---
title: "全局热键 | Microsoft Docs"
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
  - "访问键 [C++], 热键"
  - "CHotKeyCtrl 类, 全局热键"
  - "全局热键"
  - "键盘快捷键 [C++], 热键"
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 全局热键
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

全局热键与特定 nonchild 窗口。  它允许用户激活该系统的任何部分的窗口。  应用程序 [WM\_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) 通过发送消息设置特定窗口的全局热键到该窗口。  例如，在中，如果 `m_HotKeyCtrl` 为 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) 对象，`pMainWnd` 是指向窗口中激活，则这些热键按下时，可以使用以下代码将指定控件中的热键与 Windows 指向的 `pMainWnd`。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/CPP/global-hot-keys_1.cpp)]  
  
 每当用户按全局热键，指定的窗口收到指定 **SC\_HOTKEY** 作为命令类型的消息。[WM\_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360) 接收到此消息还可以激活的窗口。  由于此消息不包括有关按下的确切键的任何信息，使用该方法不允许区分可以附加到同一窗口的区别热键之间。  热键仍保持有效直至发送 **WM\_SETHOTKEY** 退出的应用程序。  
  
## 请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)