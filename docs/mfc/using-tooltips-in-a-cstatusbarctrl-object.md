---
title: "在 CStatusBarCtrl 对象中使用工具提示 | Microsoft Docs"
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
  - "CStatusBarCtrl 类, 工具提示"
  - "状态栏, 工具提示"
  - "工具提示 [C++], 在状态栏中使用"
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 CStatusBarCtrl 对象中使用工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要启用状态栏控件的工具提示，请创建具有 **SBT\_TOOLTIPS** 样式的 `CStatusBarCtrl` 对象。  
  
> [!NOTE]
>  如果使用 `CStatusBar` 对象实现状态栏，请使用 `CStatusBar::CreateEx` 函数。  它可以为嵌入的 **CStatusBarCtrl** 对象附加指定的样式。  
  
 一旦已成功创建 `CStatusBarCtrl` 对象，请使用 [CStatusBarCtrl::SetTipText](../Topic/CStatusBarCtrl::SetTipText.md) [CStatusBarCtrl::GetTipText](../Topic/CStatusBarCtrl::GetTipText.md) 和设置并检索特定窗格的提示文本。  
  
 在工具提示设置，控件显示时，部分或所有条件没有图标和文本，则文本不能显示在部件内。  工具提示在简单的模式不支持。  
  
## 请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)