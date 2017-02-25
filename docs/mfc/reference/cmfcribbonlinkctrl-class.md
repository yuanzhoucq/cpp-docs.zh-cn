---
title: "CMFCRibbonLinkCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonLinkCtrl class"
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCRibbonLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现位于功能区上的超链接。  当单击此超链接时，可以打开网页。  
  
## 语法  
  
```  
class CMFCRibbonLinkCtrl : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](../Topic/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl.md)|构造并初始化一个 `CMFCRibbonLinkCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonLinkCtrl::CopyFrom](../Topic/CMFCRibbonLinkCtrl::CopyFrom.md)|（重写 `CMFCRibbonButton::CopyFrom`。）|  
|[CMFCRibbonLinkCtrl::GetCompactSize](../Topic/CMFCRibbonLinkCtrl::GetCompactSize.md)|（重写 [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)。）|  
|[CMFCRibbonLinkCtrl::GetLink](../Topic/CMFCRibbonLinkCtrl::GetLink.md)|返回超链接的值。|  
|[CMFCRibbonLinkCtrl::GetRegularSize](../Topic/CMFCRibbonLinkCtrl::GetRegularSize.md)|（重写 [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)。）|  
|[CMFCRibbonLinkCtrl::GetToolTipText](../Topic/CMFCRibbonLinkCtrl::GetToolTipText.md)|（重写 [CMFCRibbonButton::GetToolTipText](../Topic/CMFCRibbonButton::GetToolTipText.md)。）|  
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](../Topic/CMFCRibbonLinkCtrl::IsDrawTooltipImage.md)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|  
|[CMFCRibbonLinkCtrl::OnDraw](../Topic/CMFCRibbonLinkCtrl::OnDraw.md)|（重写 [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)。）|  
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](../Topic/CMFCRibbonLinkCtrl::OnDrawMenuImage.md)|（重写 [CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)。）|  
|[CMFCRibbonLinkCtrl::OnMouseMove](../Topic/CMFCRibbonLinkCtrl::OnMouseMove.md)|（重写 `CMFCRibbonButton::OnMouseMove`。）|  
|[CMFCRibbonLinkCtrl::OnSetIcon](../Topic/CMFCRibbonLinkCtrl::OnSetIcon.md)||  
|[CMFCRibbonLinkCtrl::OpenLink](../Topic/CMFCRibbonLinkCtrl::OpenLink.md)|将打开超链接中指定的 Web 页。|  
|[CMFCRibbonLinkCtrl::SetLink](../Topic/CMFCRibbonLinkCtrl::SetLink.md)|设置超链接的值。|  
  
## 备注  
 创建超链接后，通过调用 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md) 将其添加到面板。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)  
  
## 要求  
 **标头：**afxRibbonLinkCtrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)