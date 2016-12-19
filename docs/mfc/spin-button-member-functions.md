---
title: "调节钮成员函数 | Microsoft Docs"
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
  - "CSpinButtonCtrl 类, 方法"
  - "数值调节钮控件, 方法"
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 调节钮成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有若干成员函数可用为数值调节钮控件 \(\)。[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) 使用这些函数将会旋转按钮的以下特性。  
  
-   **加速**可以调整位置的更改速率，当用户按住箭头按钮。  若要包含加速时，请使用 [SetAccel](../Topic/CSpinButtonCtrl::SetAccel.md) [GetAccel](../Topic/CSpinButtonCtrl::GetAccel.md) 和成员函数。  
  
-   **基项**可以将 \(10 或 16\) 使用的基本显示在合作者窗口的标题的位置。  若要与基本使用，请使用 [GetBase](../Topic/CSpinButtonCtrl::GetBase.md) [SetBase](../Topic/CSpinButtonCtrl::SetBase.md) 和成员函数。  
  
-   **Buddy Window** 可以动态设置合作者窗口。  若要查询或者改变控件是的合作者窗口，并使用 [GetBuddy](../Topic/CSpinButtonCtrl::GetBuddy.md) [SetBuddy](../Topic/CSpinButtonCtrl::SetBuddy.md) 成员函数。  
  
-   **位置** 您可以查询和更改位置。  若要直接与位置使用，请使用 [GetPos](../Topic/CSpinButtonCtrl::GetPos.md) [SetPos](../Topic/CSpinButtonCtrl::SetPos.md) 和成员函数。  因为合作者控件的标题可能更改 \(例如，在以下情况下是合作者编辑控件\)，使用 `GetPos` 检索当前标题并相应地调整的位置。  
  
-   **范围**可以将最大并旋转，的最低的位置按。  默认情况下，最大次数设置为 0，最小设置为 100。  因为默认最大值比默认的最小位数小于，箭头的按钮操作却不够直观。  通常，可以使用 [SetRange](../Topic/CSpinButtonCtrl::SetRange.md) 成员函数，则将设置范围。  查询范围使用 [GetRange](../Topic/CSpinButtonCtrl::GetRange.md)。  
  
## 请参阅  
 [使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [控件](../mfc/controls-mfc.md)