---
title: "CMFCRibbonStatusBar Class | Microsoft Docs"
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
  - "CMFCRibbonStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonStatusBar class"
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonStatusBar` 选件类实现可以显示功能区元素的状态栏控件。  
  
## 语法  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonStatusBar::AddDynamicElement](../Topic/CMFCRibbonStatusBar::AddDynamicElement.md)|添加动态元素添加到功能区状态栏。|  
|[CMFCRibbonStatusBar::AddElement](../Topic/CMFCRibbonStatusBar::AddElement.md)|添加新功能区组件到功能区状态栏。|  
|[CMFCRibbonStatusBar::AddExtendedElement](../Topic/CMFCRibbonStatusBar::AddExtendedElement.md)|添加一个功能区元素到功能区状态栏的扩展区域。|  
|[CMFCRibbonStatusBar::AddSeparator](../Topic/CMFCRibbonStatusBar::AddSeparator.md)|添加一个分隔符到功能区状态栏。|  
|[CMFCRibbonStatusBar::Create](../Topic/CMFCRibbonStatusBar::Create.md)|创建功能区状态栏。|  
|[CMFCRibbonStatusBar::CreateEx](../Topic/CMFCRibbonStatusBar::CreateEx.md)|用一个扩展样式创建功能区状态栏。|  
|[CMFCRibbonStatusBar::FindByID](../Topic/CMFCRibbonStatusBar::FindByID.md)||  
|[CMFCRibbonStatusBar::FindElement](../Topic/CMFCRibbonStatusBar::FindElement.md)|返回指向具有指定的命令ID.的元素|  
|[CMFCRibbonStatusBar::GetCount](../Topic/CMFCRibbonStatusBar::GetCount.md)|返回位于功能区状态栏的主区域元素的数目。|  
|[CMFCRibbonStatusBar::GetElement](../Topic/CMFCRibbonStatusBar::GetElement.md)|返回指向设置指定索引的元素。|  
|[CMFCRibbonStatusBar::GetExCount](../Topic/CMFCRibbonStatusBar::GetExCount.md)|返回位于功能区状态栏的扩展区元素的数目。|  
|[CMFCRibbonStatusBar::GetExElement](../Topic/CMFCRibbonStatusBar::GetExElement.md)|返回指针传递给指定的索引位于功能区状态栏的扩展区域的元素。|  
|[CMFCRibbonStatusBar::GetExtendedArea](../Topic/CMFCRibbonStatusBar::GetExtendedArea.md)||  
|[CMFCRibbonStatusBar::GetSpace](../Topic/CMFCRibbonStatusBar::GetSpace.md)||  
|[CMFCRibbonStatusBar::IsBottomFrame](../Topic/CMFCRibbonStatusBar::IsBottomFrame.md)||  
|[CMFCRibbonStatusBar::IsExtendedElement](../Topic/CMFCRibbonStatusBar::IsExtendedElement.md)||  
|[CMFCRibbonStatusBar::IsInformationMode](../Topic/CMFCRibbonStatusBar::IsInformationMode.md)|确定信息模式是否为功能区状态栏启动。|  
|[CMFCRibbonStatusBar::RecalcLayout](../Topic/CMFCRibbonStatusBar::RecalcLayout.md)|（重写 [CMFCRibbonBar::RecalcLayout](../Topic/CMFCRibbonBar::RecalcLayout.md)。）|  
|[CMFCRibbonStatusBar::RemoveAll](../Topic/CMFCRibbonStatusBar::RemoveAll.md)|从功能区状态栏中移除所有元素。|  
|[CMFCRibbonStatusBar::RemoveElement](../Topic/CMFCRibbonStatusBar::RemoveElement.md)|移除具有从功能区状态栏中指定的命令ID的元素。|  
|[CMFCRibbonStatusBar::SetInformation](../Topic/CMFCRibbonStatusBar::SetInformation.md)|启动或禁用功能区状态栏的信息模式。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonStatusBar::OnDrawInformation](../Topic/CMFCRibbonStatusBar::OnDrawInformation.md)|显示在功能区状态栏的信息字符串，而信息模式启动时。|  
  
## 备注  
 使用功能区状态栏中，内置的上下文菜单用户可以更改功能区元素的可见性在功能区状态栏中。  可以动态地添加或移除元素。  
  
 功能区状态栏有两个区域:一个主区域和扩展区域。  扩展区域中功能区状态栏右侧的比主要区域显示并显示在不同的颜色。  
  
 通常，状态栏的主区域显示状态通知，并且，扩展区域显示视图控件。  当用户调整功能区状态栏时，扩展区域越长越好保持可见。  
  
## 示例  
 下面的示例在 `CMFCRibbonStatusBar` 选件类演示如何使用各种方法。  此示例演示如何添加新功能区组件到功能区状态栏，添加功能区元素到功能区状态栏的扩展区域，添加分隔符和启动功能区状态栏的普通模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbar-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## 要求  
 **标头:** afxribbonstatusbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)