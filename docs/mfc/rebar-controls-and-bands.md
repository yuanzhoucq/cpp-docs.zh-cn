---
title: "Rebar 控件和带区 | Microsoft Docs"
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
  - "带区, 在 rebar 控件中"
  - "rebar 控件, 处理带区"
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Rebar 控件和带区
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

rebar 控件的主要目的是为子窗口中，公共对话框控件，菜单，工具栏容器，依此类推。  此包容由“带的概念支持”。每个带 rebar 能包含控件的句柄是条、位图、文本标签和子窗口的所有组合。  
  
 `CReBarCtrl` 类可以使用来检索和操作特定，rebar 带的信息多成员函数：  
  
-   [GetBandCount](../Topic/CReBarCtrl::GetBandCount.md) 检索当前有数 rebar 控件的。  
  
-   [GetBandInfo](../Topic/CReBarCtrl::GetBandInfo.md) 初始化信息的 **REBARBANDINFO** 结构从指定的条带。  具有相应的 [SetBandInfo](../Topic/CReBarCtrl::SetBandInfo.md) 成员函数。  
  
-   [GetRect](../Topic/CReBarCtrl::GetRect.md) 检索指定的边框。  
  
-   转到[GetRowCount](../Topic/CReBarCtrl::GetRowCount.md) 检索行的数目。rebar 控件的。  
  
-   [IDToIndex](../Topic/CReBarCtrl::IDToIndex.md) 检索指定的索引。  
  
-   [GetBandBorders](../Topic/CReBarCtrl::GetBandBorders.md) 检索带的边界。  
  
 除了处理之外，某些成员函数是，允许在将特定 rebar 的条件下进行操作。  
  
 [InsertBand](../Topic/CReBarCtrl::InsertBand.md) 和 [DeleteBand](../Topic/CReBarCtrl::DeleteBand.md) 添加和移除 rebar 带区。  [MinimizeBand](../Topic/CReBarCtrl::MinimizeBand.md) 和 [MaximizeBand](../Topic/CReBarCtrl::MaximizeBand.md) 影响特定 rebar 带的当前范围。  [MoveBand](../Topic/CReBarCtrl::MoveBand.md) 更改特定 rebar 带的索引。  [ShowBand](../Topic/CReBarCtrl::ShowBand.md) 显示或隐藏。用户 rebar 的条带。  
  
 下面的示例演示添加工具栏 \(带`m_wndToolBar`\) 到现有 rebar 控件 \(`m_wndReBar`\)。  带通过初始化 `rbi` 结构然后调用 `InsertBand` 成员函数的说明：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/CPP/rebar-controls-and-bands_1.cpp)]  
  
## 请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)