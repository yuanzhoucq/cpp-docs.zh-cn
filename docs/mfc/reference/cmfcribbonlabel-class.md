---
title: "CMFCRibbonLabel Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonLabel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonLabel class"
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMFCRibbonLabel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现功能区的非可单击文本标签。  
  
## 语法  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](../Topic/CMFCRibbonLabel::CMFCRibbonLabel.md)|构造和初始化使用指定的文本字符串的一 `CMFCRibbonLabel` 对象。|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCRibbonLabel::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCRibbonLabel::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCRibbonLabel::SetACCData](../Topic/CMFCRibbonLabel::SetACCData.md)|确定辅助功能数据为当前功能区label元素。  （重写 [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)。）|  
  
### 备注  
 在创建一个功能区标签后，将其添加到面板通过调用 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md)。  
  
 不能将功能区标签快速访问工具栏。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## 要求  
 **标头:** afxRibbonLabel.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)