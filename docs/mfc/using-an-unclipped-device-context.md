---
title: "使用未剪辑的设备上下文 | Microsoft Docs"
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
  - "MFC ActiveX 控件, 未剪辑的设备上下文"
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用未剪辑的设备上下文
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您完全确定控件不在其客户矩形外绘制，则可以通过禁用由 `COleControl`调用的电话意识到小，但能够发现速度提高到 `IntersectClipRect`。  为此，请从 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)返回的一组标志中移除 **clipPaintDC** 标志。  例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/CPP/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/using-an-unclipped-device-context_3.cpp)]  
  
 移除此标记的代码自动生成，则选择 [控件设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 页中的 **未剪辑的设备上下文 \(U\)** 选项，因此，当创建具有 MFC ActiveX 控件向导时控件。  
  
 如果使用无窗口的激活，此优化不起作用。  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)