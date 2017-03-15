---
title: "操作工具提示控件 | Microsoft Docs"
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
  - "CToolTipCtrl 类, 操作工具提示特性"
  - "工具提示 [C++], 特性"
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 操作工具提示控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CToolTipCtrl` 提供成员的一组函数控制 `CToolTipCtrl` 对象的类和工具提示窗口的各种特性。  
  
 首字母、弹出窗口以及 reshow 持续时间工具提示窗口中设置和检索与调用 [GetDelayTime](../Topic/CToolTipCtrl::GetDelayTime.md) 和 [SetDelayTime](../Topic/CToolTipCtrl::SetDelayTime.md)。  
  
 更改工具提示窗口的外观使用下面的函数：  
  
-   [GetMargin](../Topic/CToolTipCtrl::GetMargin.md) 和 [SetMargin](../Topic/CToolTipCtrl::SetMargin.md) 检索和设置工具提示边框和工具提示文本之间的宽度。  
  
-   [GetMaxTipWidth](../Topic/CToolTipCtrl::GetMaxTipWidth.md) 和 [SetMaxTipWidth](../Topic/CToolTipCtrl::SetMaxTipWidth.md) 检索和设置工具提示窗口的最大宽度。  
  
-   [GetTipBkColor](../Topic/CToolTipCtrl::GetTipBkColor.md) 和 [SetTipBkColor](../Topic/CToolTipCtrl::SetTipBkColor.md) 检索和设置工具提示窗口的背景色。  
  
-   [GetTipTextColor](../Topic/CToolTipCtrl::GetTipTextColor.md) 和 [SetTipTextColor](../Topic/CToolTipCtrl::SetTipTextColor.md) 检索和设置窗口工具提示的文本颜色。  
  
 为工具提示控件可以将关键消息通知，例如 **WM\_LBUTTONXXX** 消息，必须将消息传递给工具提示控件。  此一个中继的最佳方法是调用 [CToolTipCtrl::RelayEvent](../Topic/CToolTipCtrl::RelayEvent.md)中，所有者窗口中的 `PreTranslateMessage` 函数。  下面的示例演示一种可能的方法 \(采用工具提示控件名为 `m_ToolTip`\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/CPP/manipulating-the-tool-tip-control_1.cpp)]  
  
 直接移除工具提示窗口，请调用 [Pop](../Topic/CToolTipCtrl::Pop.md) 成员函数。  
  
## 请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)