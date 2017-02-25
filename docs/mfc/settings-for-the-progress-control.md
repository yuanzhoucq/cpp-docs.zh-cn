---
title: "进度控件的设置 | Microsoft Docs"
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
  - "CProgressCtrl 类, 设置"
  - "进度控件 [C++], 设置"
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 进度控件的设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

进度 \([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)\) 的基本设置为范围和当前位置。  范围表示操作的整个持续时间。  当前位置表示应用程序获得了在完成操作的进度。  对范围或位置的原因的任何更改重新绘制自己的进度。  
  
 默认情况下，范围设置为 0 \- 100 与初始位置设置为 0。  若要检索进度的当前范围设置，请使用 [GetRange](../Topic/CProgressCtrl::GetRange.md) 成员函数。  若要更改范围，请使用 [SetRange](../Topic/CProgressCtrl::SetRange.md) 成员函数。  
  
 若要设置定位，请使用 [SetPos](../Topic/CProgressCtrl::SetPos.md)。  若要检索当前位置，不必指定新值，请使用 [GetPos](../Topic/CProgressCtrl::GetPos.md)。  例如，在当前操作的状态可能需要查询。  
  
 若要单步执行进度的当前位置，请使用 [StepIt](../Topic/CProgressCtrl::StepIt.md)。  若要设置数量每个步骤，请使用 [SetStep](../Topic/CProgressCtrl::SetStep.md)  
  
## 请参阅  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [控件](../mfc/controls-mfc.md)