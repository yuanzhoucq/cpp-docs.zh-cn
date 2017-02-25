---
title: "优化控件绘制 | Microsoft Docs"
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
  - "MFC ActiveX 控件, 优化"
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 优化控件绘制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当控件将指示将引入所容器提供的设备上下文时，通常会选中 GDI 对象 \(如画笔、钢笔和字体\) 到设备上下文，执行其绘图操作，然后恢复以前 GDI 对象。  如果容器有绘制到相同设备上下文的多个控件，每个控件选择需要的GDI对象，如果控件不还原之前选中的对象，可以保存时间。  在所有控件绘制之后，容器可以自动还原原始对象。  
  
 若要检测容器是否支持此技术，控件可调用 [COleControl::IsOptimizedDraw](../Topic/COleControl::IsOptimizedDraw.md) 成员函数。  如果此函数返回 **TRUE**，控件可以跳过还原之前选定对象的一般步骤。  
  
 考虑包含以下\(未优化 \)`OnDraw` 函数的控件：  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/CPP/optimizing-control-drawing_1.cpp)]  
  
 在本例中的钢笔和画笔是局部变量，这意味着其析构函数将在超出范围 \(在函数结束 `OnDraw` 时\)被调用。  析构函数将尝试删除对应的 GDI 对象。  但是，如果计划将它们留在从 `OnDraw`返回的设备上下文，则不应将他们删除。  
  
 在 `OnDraw` 完成时，若要防止[CPen](../mfc/reference/cpen-class.md)和[CBrush](../mfc/reference/cbrush-class.md) 对象销毁，请将它们存储在成员变量而不是局部变量。  在控件的类声明中，将添加两个新成员变量声明：  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/CPP/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/CPP/optimizing-control-drawing_3.h)]  
  
 然后， `OnDraw`函数可以按如下方法重写：  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/CPP/optimizing-control-drawing_4.cpp)]  
  
 在每次调用 `OnDraw` 后，此方法避免钢笔和画笔的创建。  速度改进是以维护的附加实例数据为代价。  
  
 如果更改前景色或背景色属性，钢笔或画笔需要重新创建。  为此，请重写和 [OnForeColorChanged](../Topic/COleControl::OnForeColorChanged.md) [OnBackColorChanged](../Topic/COleControl::OnBackColorChanged.md) 成员函数：  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/CPP/optimizing-control-drawing_5.cpp)]  
  
 最后，清除不必要的`SelectObject`调用 ，请修改 `OnDraw` ,如下：  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/CPP/optimizing-control-drawing_6.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)   
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件：绘制 ActiveX 控件](../mfc/mfc-activex-controls-painting-an-activex-control.md)