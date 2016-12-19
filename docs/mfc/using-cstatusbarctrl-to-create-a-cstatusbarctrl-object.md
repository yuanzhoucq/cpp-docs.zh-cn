---
title: "使用 CStatusBarCtrl 创建 CStatusBarCtrl 对象 | Microsoft Docs"
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
  - "CStatusBarCtrl 类, 创建"
  - "状态栏控件, 创建"
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CStatusBarCtrl 创建 CStatusBarCtrl 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这是使用 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的典型用法示例：  
  
### 用状态栏控件部件  
  
1.  构造 `CStatusBarCtrl` 对象。  
  
2.  如果要将状态栏控件的绘图区的最小高度，请调用 [SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md) 。  
  
3.  调用 [SetBkColor](../Topic/CStatusBarCtrl::SetBkColor.md) 将状态栏控件的背景色。  
  
4.  调用 [SetParts](../Topic/CStatusBarCtrl::SetParts.md) 设置部分数目状态栏控件和各个部分右边缘坐标。  
  
5.  调用 [SetText](../Topic/CStatusBarCtrl::SetText.md) 设置文本在状态栏控件的特定部分。  消息无效更改控件的显示部分，以便新文本，然后在控件接收 `WM_PAINT` 消息时。  
  
 有时，只需要查看状态栏文本行。  在这种情况下，请调用 [SetSimple](../Topic/CStatusBarCtrl::SetSimple.md)。  这将状态栏控件。“简单”模式，显示单行文本。  
  
## 请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)