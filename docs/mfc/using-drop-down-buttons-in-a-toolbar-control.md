---
title: "使用工具栏控件中的下拉按钮 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TBN_DROPDOWN"
  - "TBSTYLE_EX_DRAWDDARROWS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl 类, 下拉按钮"
  - "工具栏中的下拉按钮"
  - "TBN_DROPDOWN 通知"
  - "TBSTYLE_EX_DRAWDDARROWS"
  - "工具栏 [C++], 下拉按钮"
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用工具栏控件中的下拉按钮
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了标准按钮之外，工具栏也有下拉按钮。  一个下拉按钮将按出现通常表示附加向下箭头下方。  
  
> [!NOTE]
>  只有当 `TBSTYLE_EX_DRAWDDARROWS` 扩展样式设置，附加向下箭头下方将出现。  
  
 当用户单击此箭头 \(或按钮，则箭头，不存在\)，`TBN_DROPDOWN` 通知消息路由到工具栏控件的父级。  然后可以处理此通知并查看弹出菜单；类似于 Internet Explorer 行为。  
  
 以下过程说明如何实现使用弹出菜单的下拉工具栏按钮：  
  
### 实现一下拉按钮  
  
1.  一旦 `CToolBarCtrl` 对象创建，使用以下代码，将 `TBSTYLE_EX_DRAWDDARROWS` 样式，例如：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  设置将为下拉按钮的所有新的 \(\) 或[InsertButton](../Topic/CToolBarCtrl::InsertButton.md)[AddButtons](../Topic/CToolBarCtrl::AddButtons.md)或现有 \([SetButtonInfo](../Topic/CToolBarCtrl::SetButtonInfo.md)\) 按钮的 `TBSTYLE_DROPDOWN` 样式。  下面的示例演示在 `CToolBarCtrl` 修改对象的现有中的按钮：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  向 `TBN_DROPDOWN` 处理程序为工具栏对象的父类。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  在新的处理程序中，显示相应的弹出菜单。  下面的代码演示一方法：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/CPP/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## 请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)