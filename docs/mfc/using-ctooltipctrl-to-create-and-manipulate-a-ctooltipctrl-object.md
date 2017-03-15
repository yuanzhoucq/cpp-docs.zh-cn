---
title: "使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl 类, using"
  - "工具提示 [C++], 创建"
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这是 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) 用法的示例：  
  
### 创建和操作 CToolTipCtrl  
  
1.  构造 `CToolTipCtrl` 对象。  
  
2.  调用 [创建](../Topic/CToolTipCtrl::Create.md) "窗口工具栏创建公共控件并将其附加到 `CToolTipCtrl` 对象。  
  
3.  调用注册工具提示控件的工具的 [AddTool](../Topic/CToolTipCtrl::AddTool.md)，这样，在工具提示中存储的信息显示，以及当光标在工具。  
  
4.  调用 [SetToolInfo](../Topic/CToolTipCtrl::SetToolInfo.md) 设置工具提示。工具维护的信息。  
  
5.  调用 [SetToolRect](../Topic/CToolTipCtrl::SetToolRect.md) 设置工具的边框。  
  
6.  调用 [HitTest](../Topic/CToolTipCtrl::HitTest.md) 测试点确定它是否位于给定的工具的边框内，并且，如果是，检索有关工具的信息。  
  
7.  调用 [GetToolCount](../Topic/CToolTipCtrl::GetToolCount.md) 检索工具的计数注册工具提示控件。  
  
## 请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)