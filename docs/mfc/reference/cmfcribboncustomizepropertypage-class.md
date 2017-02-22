---
title: "CMFCRibbonCustomizePropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "GetThisClass"
  - "CMFCRibbonCustomizePropertyPage::CreateObject"
  - "CMFCRibbonCustomizePropertyPage"
  - "CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage"
  - "CMFCRibbonCustomizePropertyPage.GetThisClass"
  - "CMFCRibbonCustomizePropertyPage.CreateObject"
  - "~CMFCRibbonCustomizePropertyPage"
  - "CreateObject"
  - "CMFCRibbonCustomizePropertyPage.~CMFCRibbonCustomizePropertyPage"
  - "CMFCRibbonCustomizePropertyPage::GetThisClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCRibbonCustomizePropertyPage destructor"
  - "CMFCRibbonCustomizePropertyPage class"
  - "CMFCRibbonCustomizePropertyPage class, 析构函数"
  - "CreateObject method"
  - "GetThisClass method"
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCRibbonCustomizePropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现 **自定义** 对话框的自定义页在基于功能区的应用程序。  
  
## 语法  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](../Topic/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage.md)|构造 `CMFCRibbonCustomizePropertyPage` 对象。|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](../Topic/CMFCRibbonCustomizePropertyPage::AddCustomCategory.md)|添加自定义类别到 **命令** 组合框。|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCRibbonCustomizePropertyPage::OnOK](../Topic/CMFCRibbonCustomizePropertyPage::OnOK.md)|调用由系统，当用户在 **自定义** 对话框中单击 **好**。|  
  
## 备注  
 如果要添加自定义命令。**自定义** 对话框，必须处理AFX\_WM\_ON\_RIBBON\_CUSTOMIZE消息。  在消息处理程序，请实例化在堆栈上的 `CMFCRibbonCustomizePropertyPage` 对象。  创建自定义指令列表，然后调用 `AddCustomCategory` 添加新的页。**自定义** 对话框。  
  
## 示例  
 下面的示例演示如何构造 `CMFCRibbonCustomizePropertyPage` 对象并将自定义类别。  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/CPP/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## 要求  
 **标头:** afxribboncustomizedialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)