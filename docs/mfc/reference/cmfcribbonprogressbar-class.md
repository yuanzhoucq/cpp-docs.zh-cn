---
title: "CMFCRibbonProgressBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonProgressBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonProgressBar class"
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonProgressBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现可视化指示较长操作的进度的控件。  
  
## 语法  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](../Topic/CMFCRibbonProgressBar::CMFCRibbonProgressBar.md)|构造和初始化 `CMFCRibbonProgressBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonProgressBar::GetPos](../Topic/CMFCRibbonProgressBar::GetPos.md)|返回当前进度。|  
|[CMFCRibbonProgressBar::GetRangeMax](../Topic/CMFCRibbonProgressBar::GetRangeMax.md)|返回当前范围的最大值。|  
|[CMFCRibbonProgressBar::GetRangeMin](../Topic/CMFCRibbonProgressBar::GetRangeMin.md)|返回当前范围的最小值。|  
|[CMFCRibbonProgressBar::GetRegularSize](../Topic/CMFCRibbonProgressBar::GetRegularSize.md)|返回功能区元素的常规大小。  （重写 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)。）|  
|[CMFCRibbonProgressBar::IsInfiniteMode](../Topic/CMFCRibbonProgressBar::IsInfiniteMode.md)|指定进度栏是否处于无限工作模式。|  
|[CMFCRibbonProgressBar::OnDraw](../Topic/CMFCRibbonProgressBar::OnDraw.md)|调用由框架绘制功能区元素。  （重写 [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)。）|  
|[CMFCRibbonProgressBar::SetInfiniteMode](../Topic/CMFCRibbonProgressBar::SetInfiniteMode.md)|在无限模式设置进度栏工作。|  
|[CMFCRibbonProgressBar::SetPos](../Topic/CMFCRibbonProgressBar::SetPos.md)|设置活动进程。|  
|[CMFCRibbonProgressBar::SetRange](../Topic/CMFCRibbonProgressBar::SetRange.md)|设置最小值和最大值。|  
  
## 备注  
 `CMFCRibbonProgressBar` 在两个模式中运行:规则和INFINITY。  在普通模式，那么，当到达最大值，进度栏从左到右进行加载和停止。  在无限模式下，进度栏从最小值重复加载到最大值。  可以使用无限模式指示操作是连续的，但是，完成时是未知的。  
  
## 示例  
 下面的示例在 `CMFCRibbonProgressBar` 选件类演示如何使用各种方法。  此示例将无限模式显示如何设置进度栏工作\(其中操作的完成时间未知\)，将最小值和最大值进度栏的，并将进度栏的当前位置。  此代码段是 [MS办公室2007中演示的示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/CPP/cmfcribbonprogressbar-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## 要求  
 **标头:** afxRibbonProgressBar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)