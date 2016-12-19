---
title: "CMFCRibbonCustomizeDialog Class | Microsoft Docs"
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
  - "GetThisClass"
  - "CMFCRibbonCustomizeDialog"
  - "~CMFCRibbonCustomizeDialog"
  - "CMFCRibbonCustomizeDialog::GetThisClass"
  - "CMFCRibbonCustomizeDialog.~CMFCRibbonCustomizeDialog"
  - "CMFCRibbonCustomizeDialog.GetThisClass"
  - "CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCRibbonCustomizeDialog destructor"
  - "CMFCRibbonCustomizeDialog class"
  - "CMFCRibbonCustomizeDialog class, 析构函数"
  - "GetThisClass method"
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonCustomizeDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显示功能区 **自定义** 页。  
  
## 语法  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](../Topic/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog.md)|构造 `CMFCRibbonCustomizeDialog` 对象。|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
  
## 备注  
 MFC自动实例化此选件类，如果不处理AFX\_WM\_ON\_RIBBON\_CUSTOMIZE消息，或者，如果返回0从消息处理程序。  
  
 如果在应用程序中使用此选件类公开功能区 **自定义** 对话框，请将其实例化并调用 `DoModal` 方法。  
  
 由于此选件类从 [CMFCPropertySheet Class](../../mfc/reference/cmfcpropertysheet-class.md)派生，使用 `CMFCPropertySheet` API，可以将自定义页。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## 要求  
 **标头:** afxribboncustomizedialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)