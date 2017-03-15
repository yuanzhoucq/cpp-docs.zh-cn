---
title: "关闭“可见时激活”选项 | Microsoft Docs"
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
  - "MFC ActiveX 控件 [C++]，激活选项"
  - "“可见时激活”选项"
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 关闭“可见时激活”选项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件有两种基本状态：活动和非活动。  传统上，这些状态通过控件是否具有窗口来区分。  一个活动控件具有一个窗口；非活动控件没有。  通过引入无窗口激活，这种区别不再通用，但仍适用于许多控件。  
  
 比较 ActiveX 控件通常执行的初始化的其他窗口中，为一个非常大的操作。  理论上，控件将延迟创建其到绝对必要的窗口。  
  
 在可见在容器中，许多控件不需要是活动的。  通常，控件可以在活动状态保持，直至用户执行例如需要成为活动的操作 \(使用鼠标，单击或按 Tab 键\)。  若要导致控件保持活动容器之前激活它，从控件的其他标志来移除 **OLEMISC\_ACTIVATEWHENVISIBLE** 标志：  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/CPP/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 **OLEMISC\_ACTIVATEWHENVISIBLE** 标志自动省略，如果关闭在 MFC ActiveX 控件向导"的 [控件设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 页中的 **Activate When Visible** 选项，当您创建控件时。  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)