---
title: "CMFCRibbonStatusBarPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonStatusBarPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonStatusBarPane class"
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCRibbonStatusBarPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonStatusBarPane` 选件类实现可以添加到功能区状态栏中显示一个功能区元素。  
  
## 语法  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](../Topic/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane.md)|构造和初始化 `CMFCRibbonStatusBarPane` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](../Topic/CMFCRibbonStatusBarPane::GetAlmostLargeText.md)|返回定义最长的文本字符串在窗格中显示，则截断的字符串。|  
|[CMFCRibbonStatusBarPane::GetTextAlign](../Topic/CMFCRibbonStatusBarPane::GetTextAlign.md)|返回当前设置文本对齐方式。|  
|[CMFCRibbonStatusBarPane::IsAnimation](../Topic/CMFCRibbonStatusBarPane::IsAnimation.md)|确定动画是否正在进行。|  
|[CMFCRibbonStatusBarPane::IsExtended](../Topic/CMFCRibbonStatusBarPane::IsExtended.md)|确定窗格是否位于功能区状态栏的扩展区域。|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](../Topic/CMFCRibbonStatusBarPane::OnDrawBorder.md)|（重写 [CMFCRibbonButton::OnDrawBorder](../Topic/CMFCRibbonButton::OnDrawBorder.md)。）|  
|[CMFCRibbonStatusBarPane::OnFillBackground](../Topic/CMFCRibbonStatusBarPane::OnFillBackground.md)|（重写 [CMFCRibbonButton::OnFillBackground](../Topic/CMFCRibbonButton::OnFillBackground.md)。）|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](../Topic/CMFCRibbonStatusBarPane::SetAlmostLargeText.md)|定义在窗格中显示，则截断的最长的文本字符串。|  
|[CMFCRibbonStatusBarPane::SetAnimationList](../Topic/CMFCRibbonStatusBarPane::SetAnimationList.md)|分配到图像列表可用于动画使用的窗格。|  
|[CMFCRibbonStatusBarPane::SetTextAlign](../Topic/CMFCRibbonStatusBarPane::SetTextAlign.md)|设置文本对齐方式。|  
|[CMFCRibbonStatusBarPane::StartAnimation](../Topic/CMFCRibbonStatusBarPane::StartAnimation.md)|启动分配给窗格的动画。|  
|[CMFCRibbonStatusBarPane::StopAnimation](../Topic/CMFCRibbonStatusBarPane::StopAnimation.md)|停止分配给窗格的动画。  .|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](../Topic/CMFCRibbonStatusBarPane::OnFinishAnimation.md)|调用由结构，当分配给窗格的动画停止。|  
  
## 示例  
 下面的示例在 `CMFCRibbonStatusBarPane` 选件类演示如何使用各种方法。  此示例演示如何构造 `CMFCRibbonStatusBarPane` 对象，并设置状态栏窗格的标签的文本对齐方式，定义在状态栏窗格中显示，则截断的最长的文本，附加到可用于动画使用的状态栏窗格图像列表，并启动动画。  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## 要求  
 **标头:** afxribbonstatusbarpane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar Class](../../mfc/reference/cmfcribbonstatusbar-class.md)