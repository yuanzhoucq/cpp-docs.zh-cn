---
title: "CMFCFontInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFontInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFontInfo class"
  - "CMFCFontInfo::CMFCFontInfo constructor"
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCFontInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCFontInfo` 选件类描述名称和字体的其他属性。  
  
## 语法  
  
```  
class CMFCFontInfo : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCFontInfo`|构造 `CMFCFontInfo` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCFontInfo::GetFullName](../Topic/CMFCFontInfo::GetFullName.md)|检索字体及其字符集\(脚本\)的连接的名称。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCFontInfo::m\_nCharSet](../Topic/CMFCFontInfo::m_nCharSet.md)|指定该字符集的值\(脚本\)与字体。|  
|[CMFCFontInfo::m\_nPitchAndFamily](../Topic/CMFCFontInfo::m_nPitchAndFamily.md)|指定字体的间距和系列的值。|  
|[CMFCFontInfo::m\_nType](../Topic/CMFCFontInfo::m_nType.md)|指定字体的类型的值。|  
|[CMFCFontInfo::m\_strName](../Topic/CMFCFontInfo::m_strName.md)|字体的名称;例如，**Arial**。|  
|[CMFCFontInfo::m\_strScript](../Topic/CMFCFontInfo::m_strScript.md)|字符集\(脚本\)的名称与字体。|  
  
## 备注  
 可以附加到 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 选件类的项 `CMFCFontInfo` 对象。  调用 [CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md) 方法以检索指向 `CMFCFontInfo` 对象。  
  
## 示例  
 下面的示例演示如何使用 `CMFCFontInfo` 选件类的各种成员。  示例演示如何访问演示如何从获取 `CMFCRibbonFontComboBox`的一 `CMFCFontInfo` 对象和局部变量。  此示例是 [MSOffice 2007中演示的示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/CPP/cmfcfontinfo-class_1.cpp)]  
  
## 要求  
 **标头:** afxtoolbarfontcombobox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox Class](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)