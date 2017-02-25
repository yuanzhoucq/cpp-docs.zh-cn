---
title: "CMFCToolTipInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolTipInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolTipInfo class"
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCToolTipInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存储有关工具提示视觉外观的信息。  
  
## 语法  
  
```  
class CMFCToolTipInfo  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolTipInfo::operator\=](../Topic/CMFCToolTipInfo::operator=.md)||  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolTipInfo::m\_bBalloonTooltip](../Topic/CMFCToolTipInfo::m_bBalloonTooltip.md)|指示工具提示是否具有气球外观的布尔变量。|  
|[CMFCToolTipInfo::m\_bBoldLabel](../Topic/CMFCToolTipInfo::m_bBoldLabel.md)|指示工具提示标签是否以粗体显示的布尔变量。|  
|[CMFCToolTipInfo::m\_bDrawDescription](../Topic/CMFCToolTipInfo::m_bDrawDescription.md)|指示工具提示是否包含说明的布尔变量。|  
|[CMFCToolTipInfo::m\_bDrawIcon](../Topic/CMFCToolTipInfo::m_bDrawIcon.md)|指示工具提示是否包含图标的布尔变量。|  
|[CMFCToolTipInfo::m\_bDrawSeparator](../Topic/CMFCToolTipInfo::m_bDrawSeparator.md)|指示分隔符是否显示在工具提示标签和工具提示说明之间的布尔变量。|  
|[CMFCToolTipInfo::m\_bRoundedCorners](../Topic/CMFCToolTipInfo::m_bRoundedCorners.md)|指示工具提示是否具有圆角的布尔变量。|  
|[CMFCToolTipInfo::m\_bVislManagerTheme](../Topic/CMFCToolTipInfo::m_bVislManagerTheme.md)|指示工具提示的外观是否应由虚拟管理器控制的布尔变量。（请参阅 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)）。|  
|[CMFCToolTipInfo::m\_clrBorder](../Topic/CMFCToolTipInfo::m_clrBorder.md)|工具提示边框的颜色。|  
|[CMFCToolTipInfo::m\_clrFill](../Topic/CMFCToolTipInfo::m_clrFill.md)|工具提示背景的颜色。|  
|[CMFCToolTipInfo::m\_clrFillGradient](../Topic/CMFCToolTipInfo::m_clrFillGradient.md)|工具提示中渐变填充的颜色。|  
|[CMFCToolTipInfo::m\_clrText](../Topic/CMFCToolTipInfo::m_clrText.md)|工具提示中的文本颜色。|  
|[CMFCToolTipInfo::m\_nGradientAngle](../Topic/CMFCToolTipInfo::m_nGradientAngle.md)|工具提示中渐变填充的角度。|  
|[CMFCToolTipInfo::m\_nMaxDescrWidth](../Topic/CMFCToolTipInfo::m_nMaxDescrWidth.md)|工具提示中说明的最大可能宽度（以像素为单位）。|  
  
## 备注  
 同时使用 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)、`CMFCToolTipInfo` 和 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)，以在应用程序中实现自定义的工具提示。  有关如何使用这些工具提示类的示例，请参阅 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md) 主题。  
  
## 示例  
 下面的示例演示了如何在 `CMFCToolTipInfo` 类中设置多个成员变量的值的方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/CPP/cmfctooltipinfo-class_1.cpp)]  
  
## 继承层次结构  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## 要求  
 **标头：**afxtooltipctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)