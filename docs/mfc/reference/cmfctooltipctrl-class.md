---
title: "CMFCToolTipCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolTipCtrl class"
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基于 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的扩展工具提示实现。  基于 `CMFCToolTipCtrl` 类的工具提示可显示图标、标签和说明。  可以使用渐变填充、自定义文本和边框颜色、粗体文本、圆角或气球样式来自定义可视外观。  
  
## 语法  
  
```  
class CMFCToolTipCtrl : public CToolTipCtrl  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolTipCtrl::GetIconSize](../Topic/CMFCToolTipCtrl::GetIconSize.md)|返回工具提示中的图标大小。|  
|[CMFCToolTipCtrl::GetParams](../Topic/CMFCToolTipCtrl::GetParams.md)|返回工具提示的显示设置。|  
|[CMFCToolTipCtrl::OnDrawBorder](../Topic/CMFCToolTipCtrl::OnDrawBorder.md)|绘制工具提示的边框。|  
|[CMFCToolTipCtrl::OnDrawDescription](../Topic/CMFCToolTipCtrl::OnDrawDescription.md)||  
|[CMFCToolTipCtrl::OnDrawIcon](../Topic/CMFCToolTipCtrl::OnDrawIcon.md)|显示工具提示中的图标。|  
|[CMFCToolTipCtrl::OnDrawLabel](../Topic/CMFCToolTipCtrl::OnDrawLabel.md)|绘制工具提示标签或计算标签的大小。|  
|[CMFCToolTipCtrl::OnDrawSeparator](../Topic/CMFCToolTipCtrl::OnDrawSeparator.md)|绘制工具提示中标签和说明之间的分隔符。|  
|[CMFCToolTipCtrl::OnFillBackground](../Topic/CMFCToolTipCtrl::OnFillBackground.md)|填充工具提示的背景。|  
|[CMFCToolTipCtrl::SetDescription](../Topic/CMFCToolTipCtrl::SetDescription.md)|设置将由工具提示显示的说明。|  
|[CMFCToolTipCtrl::SetFixedWidth](../Topic/CMFCToolTipCtrl::SetFixedWidth.md)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](../Topic/CMFCToolTipCtrl::SetHotRibbonButton.md)||  
|[CMFCToolTipCtrl::SetLocation](../Topic/CMFCToolTipCtrl::SetLocation.md)||  
|[CMFCToolTipCtrl::SetParams](../Topic/CMFCToolTipCtrl::SetParams.md)|通过使用 `CMFCToolTipInfo` 对象指定工具提示的视觉外观。|  
  
## 备注  
 结合使用 `CMFCToolTipCtrl`、`CMFCToolTipInfo`和 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md) 对象以在应用程序中实现自定义的工具提示。  
  
 例如，若要使用气球样式的工具提示，请按照下列步骤执行：  
  
 1.  使用 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) 方法以初始化应用程序中的工具提示管理器。  
  
 2.  创建 `CMFCToolTipInfo` 结构，以指定所需的视觉样式：  
  
```  
CMFCToolTipInfo params;  
 params.m_bBoldLabel = FALSE;  
 params.m_bDrawDescription = FALSE;  
 params.m_bDrawIcon = FALSE;  
 params.m_bRoundedCorners = TRUE;  
 params.m_bDrawSeparator = FALSE;  
 if (m_bCustomColors)  
 {  
  params.m_clrFill = RGB (255, 255, 255);  
  params.m_clrFillGradient = RGB (228, 228, 240);  
  params.m_clrText = RGB (61, 83, 80);  
  params.m_clrBorder = RGB (144, 149, 168);  
 }  
```  
  
 3.  使用 [CTooltipManager::SetTooltipParams](../Topic/CTooltipManager::SetTooltipParams.md) 方法通过使用 `CMFCToolTipInfo` 对象中定义的样式设置应用程序中所有工具提示的视觉样式：  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);  
```  
  
 你也可以从 `CMFCToolTipCtrl` 派生新类以控制工具提示行为和呈现。  若要指定新的工具提示控制类，请使用 `CTooltipManager::SetTooltipParams` 方法：  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
  
 若要恢复默认的工具提示控件类并将工具提示外观重置回其默认状态，请指定运行时类中的 NULL 和 `SetTooltipParams` 的工具提示信息参数：  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL, NULL);  
```  
  
## 示例  
 下面的示例演示了如何构造 `CMFCToolTipCtrl` 对象、如何设置工具提示显示的说明以及如何设置工具提示控件的宽度。  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/CPP/cmfctooltipctrl-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## 要求  
 **标头：**afxtooltipctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)   
 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)