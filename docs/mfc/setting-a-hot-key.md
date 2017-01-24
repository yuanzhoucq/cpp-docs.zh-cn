---
title: "设置热键 | Microsoft Docs"
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
  - "CHotKeyCtrl 类, 设置热键"
  - "键盘快捷键 [C++], 热键"
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 设置热键
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

应用程序可以使用以下两种方式之一使用一热键 \([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)\) 控件提供的信息：  
  
-   通过 [WM\_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) 发送消息设置激活的窗口 nonchild 全局热键到要激活的窗口。  
  
-   通过调用 Windows 函数设置一个给定线程热键 [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## 请参阅  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控件](../mfc/controls-mfc.md)