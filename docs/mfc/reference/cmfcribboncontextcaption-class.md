---
title: "CMFCRibbonContextCaption Class | Microsoft Docs"
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
  - "CMFCRibbonContextCaption"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonContextCaption class"
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonContextCaption Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现显示在功能区类别或上下文类别顶部的彩色标题。  
  
## 语法  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|`CMFCRibbonContextCaption::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCRibbonContextCaption::GetColor](../Topic/CMFCRibbonContextCaption::GetColor.md)|返回标题栏的颜色。|  
|[CMFCRibbonContextCaption::GetRightTabX](../Topic/CMFCRibbonContextCaption::GetRightTabX.md)||  
|`CMFCRibbonContextCaption::GetThisClass`|由框架用于获取指向与此类类型关联的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象的指针。|  
  
## 备注  
 不能直接实例化此类。  [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) 类在内部使用此类以将颜色添加到功能区类别。  
  
 若要设置功能区类别的颜色，请调用 [CMFCRibbonCategory::SetTabColor](../Topic/CMFCRibbonCategory::SetTabColor.md)。  若要设置上下文类别的颜色，请调用 [CMFCRibbonBar::AddContextCategory](../Topic/CMFCRibbonBar::AddContextCategory.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## 要求  
 **标头：**afxRibbonBar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)