---
title: "MFC 中的状态栏实现 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COldStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COldStatusBar 类"
  - "CStatusBar 类, 和 CStatusBarCtrl 类"
  - "CStatusBar 类, 和 MFC 状态栏"
  - "CStatusBarCtrl 类, 和 CStatusBar 类"
  - "CStatusBarCtrl 类, 和 MFC 状态栏"
  - "状态栏, 和 CStatusBarCtrl 类"
  - "状态栏, 向后兼容性"
  - "状态栏, 在 MFC 中实现"
  - "状态栏, 对于 COldStatusBar 类而言是旧的"
  - "状态栏, Windows 95 实现"
  - "状态指示器"
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的状态栏实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CStatusBar](../mfc/reference/cstatusbar-class.md) 对象与文本行输出窗格的控件条。  输出窗格通常用作消息行将状态指示器。  包括示例简短说明选择的菜单命令和指示符显示 Scroll Lock、Num Lock 和其他键的状态的菜单帮助消息行。  
  
 使用 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)类，自 MFC 4.0 版，状态栏会实现，封装状态栏公共控件。  对于向后兼容性，MFC 中保留类 **COldStatusBar**的更早的状态栏。实现。  MFC 早期版本的文档描述 **COldStatusBar**`CStatusBar`下。  
  
 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)，成员函数为新 MFC 4.0，可以利用自定义状态栏以及附加功能的 Windows 公共控件的支持。  `CStatusBar` 成员函数提供了最新 Windows 公共控件的功能；但是，当您调用 `GetStatusBarCtrl`时，可以为状态栏的状态栏的特性。  当您调用 `GetStatusBarCtrl`，它将返回对 `CStatusBarCtrl` 对象的引用。  可以使用该引用操作状态栏控件。  
  
 下图演示多个指示符的状态栏。  
  
 ![状态栏](../mfc/media/vc37dy1.png "vc37DY1")  
状态栏  
  
 与工具栏，那么，当框架窗口构造时，状态栏对象在它的父框架窗口嵌入和自动构造。  当销毁时，像任何控件条，自动销毁状态栏父帧。  
  
## 您想进一步了解什么？  
  
-   [更新状态栏窗格的文本](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   MFC 类和 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)[CStatusBar](../mfc/reference/cstatusbar-class.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
-   [对话栏](../mfc/dialog-bars.md)  
  
-   [工具栏 \(MFC 工具栏实现\)](../mfc/mfc-toolbar-implementation.md)  
  
## 请参阅  
 [状态栏](../mfc/status-bars.md)