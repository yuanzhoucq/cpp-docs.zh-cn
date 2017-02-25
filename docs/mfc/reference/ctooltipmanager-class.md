---
title: "CTooltipManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTooltipManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTooltipManager class"
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CTooltipManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

维护有关工具提示的运行时信息。  `CTooltipManager` 类在每个应用程序中实例化一次。  
  
## 语法  
  
```  
class CTooltipManager : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTooltipManager::CreateToolTip](../Topic/CTooltipManager::CreateToolTip.md)|为指定的 Windows 控件类型创建工具提示控件。|  
|[CTooltipManager::DeleteToolTip](../Topic/CTooltipManager::DeleteToolTip.md)|删除工具提示控件。|  
|[CTooltipManager::SetTooltipParams](../Topic/CTooltipManager::SetTooltipParams.md)|自定义指定 Windows 控件类型工具提示的可视外观。|  
|[CTooltipManager::SetTooltipText](../Topic/CTooltipManager::SetTooltipText.md)|设置工具提示控件的文本和说明。|  
|[CTooltipManager::UpdateTooltips](../Topic/CTooltipManager::UpdateTooltips.md)||  
  
## 备注  
 同时使用 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)、`CMFCToolTipInfo` 和 `CTooltipManager`，以在应用程序中实现自定义的工具提示。  有关如何使用这些工具提示类的示例，请参阅 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md) 主题。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## 要求  
 **标头：**afxtooltipmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)