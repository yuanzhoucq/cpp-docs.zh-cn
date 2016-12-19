---
title: "提供无闪烁激活 | Microsoft Docs"
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
  - "激活 [C++], 无闪烁"
  - "闪烁, MFC ActiveX 控件"
  - "MFC ActiveX 控件 [C++], 无闪烁"
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提供无闪烁激活
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果控件处于活动和活动绘制相同状态 \(和不使用无窗口中激活\)，可以消除通常发生，当在停用以及活动状态之间进行过渡的绘图操作及随附的视觉闪烁。  为此，在组的 **noFlickerActivate** 标志。[COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)返回。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/CPP/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-flicker-free-activation_3.cpp)]  
  
 为包含此标记的代码自动生成，则选择 [控件设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 页中的 **无闪烁激活 \(V\)** 选项，当创建具有 MFC ActiveX 控件向导时控件。  
  
 如果使用无窗口的激活，此优化不起作用。  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)