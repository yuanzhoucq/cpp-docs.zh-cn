---
title: "创建工具提示的方法 | Microsoft Docs"
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
  - "CToolTipCtrl 类, 创建工具提示"
  - "工具提示 [C++], 创建"
  - "工具提示 [C++], 工具提示控件"
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建工具提示的方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供三类创建并管理工具提示控件：[CWnd](../mfc/reference/cwnd-class.md)[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)、、和。  在工具提示的这些类成员函数包装 Windows 公共控件 API。  `CToolBarCtrl` 类和 `CToolTipCtrl` 类从 `CWnd`类派生。  
  
 `CWnd` 提供四个成员函数创建和管理工具提示：[EnableToolTips](../Topic/CWnd::EnableToolTips.md)[CancelToolTips](../Topic/CWnd::CancelToolTips.md)[FilterToolTipMessage](../Topic/CWnd::FilterToolTipMessage.md)[OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)、、和。  参见这些个别成员函数有关它们的更多信息来实现工具提示。  
  
 使用 `CToolBarCtrl`，可以创建工具栏，直接使用以下成员函数，则可以实现该工具栏的工具提示：[GetToolTips](../Topic/CToolBarCtrl::GetToolTips.md) 和 [SetToolTips](../Topic/CToolBarCtrl::SetToolTips.md)。  参见这些个别成员函数\) 和 [处理工具提示通知](../mfc/handling-tool-tip-notifications.md) 有关它们的更多信息来实现工具提示。  
  
 `CToolTipCtrl`提供 Windows 公共 IP 地址控件的功能。  一个工具提示控件可以为多个工具的信息。  工具是一个窗口，如子窗口或控件或在窗口的工作区显示您的应用程序定义的矩形区域。  [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) 类从 `CToolTipCtrl` 派生并提供其他的可视样式和功能。  
  
## 请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)