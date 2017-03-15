---
title: "工具提示控件的设置 | Microsoft Docs"
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
  - "工具提示 [C++], 激活"
  - "CToolTipCtrl 类, 设置"
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 工具提示控件的设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以将工具提示控件 \([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)\) 设置为活动或非活动。 如果将其设置为活动状态，当光标位于工具上时，将显示工具提示控件。 如果将其设置为非活动状态，即使光标位于工具上时，也不会显示工具提示控件。 调用 [Activate](../Topic/CToolTipCtrl::Activate.md) 以激活或停用工具提示控件。  
  
 无论工具提示控件的所有者窗口处于活动还是非活动状态，均可以在光标位于工具上时，通过使用 **TTS\_ALWAYSTIP** 样式来将活动的工具提示设置为显示工作提示。 如果不使用此样式，工具提示控件将在工具的所有者窗口处于活动状态时显示，当其处于非活动状态时则不显示。  
  
 大多数应用程序均有工具栏，工具栏中的工具与菜单命令对应。 对于此类工具，工具提示控件可以方便地显示与相应菜单项相同的文本。 系统自动去除传递到工具提示控件的所有字符串的与号 \(&\) 加速器字符，除非控件具有 **TTS\_NOPREFIX** 样式。  
  
## 请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)