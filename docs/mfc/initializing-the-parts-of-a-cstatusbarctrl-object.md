---
title: "初始化 CStatusBarCtrl 对象的组成部分 | Microsoft Docs"
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
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl 类, 声明部件"
  - "CStatusBarCtrl 类, 简单模式"
  - "图标, 在状态栏中使用"
  - "简单状态栏"
  - "状态栏, 声明部件"
  - "状态栏, 图标"
  - "状态栏, 简单模式"
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始化 CStatusBarCtrl 对象的组成部分
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，使用一个单独窗格，状态栏显示状态信息。  这些窗格 \(也称部件\) 可以包含文本字符串，或者两个图标。  
  
 使用 [SetParts](../Topic/CStatusBarCtrl::SetParts.md) 定义的部件和长度，状态栏会有。  在创建状态栏的部分之后，请调用 [SetText](../Topic/CStatusBarCtrl::SetText.md) [SetIcon](../Topic/CStatusBarCtrl::SetIcon.md) 设置和文本或图标状态栏的特定部分的。  一个部件已成功设置，控件会重新绘制。  
  
 下面的示例使用第二部分初始化中现有的 `CStatusBarCtrl` 对象 \(`m_StatusBarCtrl`\) 包含四个窗格然后将图标 \(IDI\_I CON1\) 和某些文本。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/CPP/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 有关设置 `CStatusBarCtrl` 对象模式的更多信息。简单，请参见 [设置 CStatusBarCtrl 对象的模式](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
## 请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)