---
title: "工具栏控件样式 | Microsoft Docs"
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
  - "工具栏控件样式"
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 16
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 工具栏控件样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) 具有一组确定按钮外观和行为样式标志。  通过调用 [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)设置这些标志的组合。  本主题列出样式标志值及它们的含义。  
  
## 属性值  
 下面的值决定控件代表按钮的类型：  
  
 TBBS\_BUTTON  
 标准按钮 \(默认\)。  
  
 TBBS\_CHECKBOX  
 复选框。  
  
 TBBS\_CHECKGROUP  
 复选框组的开始。  
  
 TBBS\_GROUP  
 按钮组的开始。  
  
 TBBS\_SEPARATOR  
 分隔符。  
  
 下列值表示控件的当前状态：  
  
 TBBS\_CHECKED  
 此复选框处于选中状态。  
  
 TBBS\_DISABLED  
 控件被禁用。  
  
 TBBS\_INDETERMINATE  
 复选框处于不确定状态。  
  
 TBBS\_PRESSED  
 该按钮处于按下状态。  
  
 下列值更改按钮在工具栏中的布局：  
  
 TBBS\_BREAK  
 放置项在新行或新的列，而不分馏柱。  
  
## 备注  
 当前样式存储在[CMFCToolBarButton::m\_nStyle](../Topic/CMFCToolBarButton::m_nStyle.md)中。  不要直接设置 `m_nStyle` 的新值，因为一些派生类执行其他处理您在调用 `SetStyles`时。  
  
 视觉管理器在每个状态中确定按钮外观。  有关更多信息，请参见[可视化管理器](../../mfc/visualization-manager.md)。  
  
## 要求  
 **页眉：** afxtoolbarbutton.h  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [可视化管理器](../../mfc/visualization-manager.md)