---
title: "CMFCRibbonCheckBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonCheckBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonCheckBox class"
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCRibbonCheckBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonCheckBox` 类实现可添加到功能区面板、快速访问工具栏或弹出菜单的复选框。  
  
## 语法  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](../Topic/CMFCRibbonCheckBox::CMFCRibbonCheckBox.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonCheckBox::GetCompactSize](../Topic/CMFCRibbonCheckBox::GetCompactSize.md)|（重写 [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)。）|  
|[CMFCRibbonCheckBox::GetIntermediateSize](../Topic/CMFCRibbonCheckBox::GetIntermediateSize.md)|（重写 [CMFCRibbonButton::GetIntermediateSize](../Topic/CMFCRibbonButton::GetIntermediateSize.md)。）|  
|[CMFCRibbonCheckBox::GetRegularSize](../Topic/CMFCRibbonCheckBox::GetRegularSize.md)|（重写 [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)。）|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](../Topic/CMFCRibbonCheckBox::IsDrawTooltipImage.md)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|  
|[CMFCRibbonCheckBox::OnDraw](../Topic/CMFCRibbonCheckBox::OnDraw.md)|（重写 [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)。）|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](../Topic/CMFCRibbonCheckBox::OnDrawMenuImage.md)|（重写 [CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)。）|  
|[CMFCRibbonCheckBox::OnDrawOnList](../Topic/CMFCRibbonCheckBox::OnDrawOnList.md)|（重写 `CMFCRibbonButton::OnDrawOnList`。）|  
|[CMFCRibbonCheckBox::SetACCData](../Topic/CMFCRibbonCheckBox::SetACCData.md)|（重写 [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)。）|  
  
## 备注  
 若要在应用程序中使用 `CMFCRibbonCheckBox`，请向代码添加以下构造函数：  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
  
 其中 `nID` 是复选框命令 ID，`lpszText` 是复选框的文本标签。  
  
 可以使用 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md) 向功能区面板添加复选框。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## 要求  
 **标头:** afxribboncheckbox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)