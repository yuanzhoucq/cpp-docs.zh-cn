---
title: "CMFCTabToolTipInfo Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabToolTipInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabToolTipInfo struct"
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCTabToolTipInfo Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此结构提供有关用户旋转的MDI选项的信息。  
  
## 语法  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## 成员  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCTabToolTipInfo::m\_nTabIndex](../Topic/CMFCTabToolTipInfo::m_nTabIndex.md)|指定选项卡控件的索引。|  
|[CMFCTabToolTipInfo::m\_pTabWnd](../Topic/CMFCTabToolTipInfo::m_pTabWnd.md)|对于可选控件的指针。|  
|[CMFCTabToolTipInfo::m\_strText](../Topic/CMFCTabToolTipInfo::m_strText.md)|工具提示文本。|  
  
## 备注  
 为 `CMFCTabToolTipInfo` 结构的指针将作为 `AFX_WM_ON_GET_TAB_TOOLTIP` 消息的参数。  当MDI启用选项和在选项卡控件时，用户悬停此消息生成。  
  
## 示例  
 下面的示例演示 `CMFCTabToolTipInfo` 如何在 [MDITabsDemo示例:MFC选项卡式MDI应用程序](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/CPP/cmfctabtooltipinfo-structure_1.cpp)]  
  
## 继承层次结构  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## 要求  
 **标头:** afxbasetabctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx::EnableMDITabs](../Topic/CMDIFrameWndEx::EnableMDITabs.md)   
 [CMDITabInfo::m\_bTabCustomTooltips](../Topic/CMDITabInfo::m_bTabCustomTooltips.md)