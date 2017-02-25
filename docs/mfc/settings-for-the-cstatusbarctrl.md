---
title: "CStatusBarCtrl 的设置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "CStatusBarCtrl 类, 设置"
  - "状态栏控件, 设置"
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CStatusBarCtrl 的设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) "状态"窗口的默认位置位于父窗口的底部，但您可指定 `CCS_TOP` 样式使其显示在父窗口的工作区的顶部。  
  
 还可以指定 **SBARS\_SIZEGRIP**。样式包含调整手柄在 `CStatusBarCtrl` 状态窗口的右端。  调整手柄类似大小调整边框；是用户可以通过单击和拖动来调整父窗口的矩形区域。  
  
> [!NOTE]
>  如果组合使用 `CCS_TOP` 和样式，发生 **SBARS\_SIZEGRIP** 的调整手柄不工作，即使系统绘制在"状态"窗口。  
  
 "状态"窗口的窗口过程会自动设置控件窗口的初始大小和位置。  宽度与其父窗口的工作区。  高度根据当前选择到"状态"窗口的上下文和设备在窗口边框的宽度字体的指标。  
  
 窗口过程自动调整窗口范围状态的，只要它接收 `WM_SIZE` 消息。  通常，当父，窗口大小的改变时，父 `WM_SIZE` 消息发送到"状态"窗口。  
  
 通过调用 [SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md)设置状态窗口中绘图区的最小高度，指定最小高度 \(以像素为单位\)。  绘图区域不包括窗口边框。  
  
 通过调用 [GetBorders](../Topic/CStatusBarCtrl::GetBorders.md)状态检索窗口边框的宽度。  该成员函数的包含指针到接收的水平、垂直范围的边界和边框的宽度矩形之间的三个元素的数组。  
  
## 请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)