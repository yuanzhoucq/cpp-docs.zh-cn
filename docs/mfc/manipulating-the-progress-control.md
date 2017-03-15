---
title: "操作进度控件 | Microsoft Docs"
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
  - "控制进度控件"
  - "CProgressCtrl 类, 操作"
  - "CProgressCtrl 类, using"
  - "CProgressCtrl 类, 处理"
  - "进度控件 [C++], 操作"
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 操作进度控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有三种方式更改进度 \([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)\) 的当前位置。  
  
-   位置可以按预设的增量更改量。  
  
-   位置可以由任意数量更改。  
  
-   位置可以更改为特定值。  
  
### 若要改变位置请总计预设。  
  
1.  使用 [SetStep](../Topic/CProgressCtrl::SetStep.md) 成员函数将递增量。  默认情况下，此值为 10。  此值通常设置，其中一个控件的初始设置。   可以是负值。  
  
2.  使用 [StepIt](../Topic/CProgressCtrl::StepIt.md) 成员函数添加位置。  这将导致控件重新绘制自身。  
  
    > [!NOTE]
    >  `StepIt` 导致位置包装。  例如为 1 \- 100 范围内，第 20 步和位置 90，`StepIt` 10。将位置设置为 .  
  
### 改变位置由一个任意数量  
  
1.  使用 [OffsetPos](../Topic/CProgressCtrl::OffsetPos.md) 成员函数更改位置。  `OffsetPos` 会接受负数值。  
  
    > [!NOTE]
    >  `OffsetPos`，与 `StepIt`不同的是，不会包装位置。  调整新的位置保持在范围内。  
  
### 改变位置为特定值。  
  
1.  使用 [SetPos](../Topic/CProgressCtrl::SetPos.md) 成员函数位置设置为特定值。  如有必要，调整新位置的范围内。  
  
 通常，输出进度为单独使用。  若要获取当前位置，不必指定新值，请使用 [GetPos](../Topic/CProgressCtrl::GetPos.md)。  
  
## 请参阅  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [控件](../mfc/controls-mfc.md)