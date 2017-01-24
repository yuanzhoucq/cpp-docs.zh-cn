---
title: "CMFCCustomColorsPropertyPage Class | Microsoft Docs"
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
  - "CMFCCustomColorsPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCustomColorsPropertyPage class"
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCustomColorsPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示可以选择在颜色对话框的自定义颜色的属性页。  
  
## 语法  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|默认构造函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCCustomColorsPropertyPage::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCCustomColorsPropertyPage::Setup](../Topic/CMFCCustomColorsPropertyPage::Setup.md)|设置属性页的颜色分量。|  
  
### 备注  
 `CMFCColorDialog` 选件类使用此选件类将自定义颜色属性页。  有关 `CMFCColorDialog`的更多信息，请参见[CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)。  
  
## 示例  
 下面的示例演示如何构造 `CMFCCustomColorsPropertyPage` 对象和设置属性页的颜色分量。  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/CPP/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## 要求  
 **标头:** afxcustomcolorspropertypage.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage Class](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)