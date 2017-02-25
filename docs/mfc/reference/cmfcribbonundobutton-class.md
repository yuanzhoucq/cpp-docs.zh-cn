---
title: "CMFCRibbonUndoButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonUndoButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonUndoButton class"
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCRibbonUndoButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonUndoButton` 选件类实现下拉列表包含最新用户命令的按钮。  用户可以选择一个或多个新命令从下拉列表设置为重做或移除它们。  
  
## 语法  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](../Topic/CMFCRibbonUndoButton::CMFCRibbonUndoButton.md)|构造新 `CMFCRibbonUndoButton` 对象使用命令ID指定，文本标签，然后从图像的图像列表父对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonUndoButton::AddUndoAction](../Topic/CMFCRibbonUndoButton::AddUndoAction.md)|新事件添加到事件列表。|  
|[CMFCRibbonUndoButton::CleanUpUndoList](../Topic/CMFCRibbonUndoButton::CleanUpUndoList.md)|清除操作列表，下拉列表。|  
|[CMFCRibbonUndoButton::GetActionNumber](../Topic/CMFCRibbonUndoButton::GetActionNumber.md)|确定用户从下拉列表项的数目。|  
|[CMFCRibbonUndoButton::HasMenu](../Topic/CMFCRibbonUndoButton::HasMenu.md)|指示对象是否包含菜单。|  
  
## 备注  
 `CMFCRibbonUndoButton` 选件类使用堆栈表示下拉列表。  
  
## 示例  
 下面的示例演示如何构造对象 `CMFCRibbonUndoButton` 选件类，并添加新事件。事件列表。  此代码段是 [功能区小工具示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/CPP/cmfcribbonundobutton-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## 要求  
 **标头:** afxribbonundobutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)