---
title: "CMFCPropertyGridFontProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridFontProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridFontProperty class"
  - "CMFCPropertyGridFontProperty::FormatProperty method"
  - "CMFCPropertyGridFontProperty::OnClickButton method"
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCPropertyGridFontProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyGridFileProperty` 选件类支持属性列表将字体选择对话框的控件项目。  
  
## 语法  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](../Topic/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty.md)|构造 `CMFCPropertyGridFontProperty` 对象。|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|设置属性值的文本表示形式。  （重写 [CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md)。）|  
|[CMFCPropertyGridFontProperty::GetColor](../Topic/CMFCPropertyGridFontProperty::GetColor.md)|检索用户从字体对话框中选择的字体。|  
|[CMFCPropertyGridFontProperty::GetLogFont](../Topic/CMFCPropertyGridFontProperty::GetLogFont.md)|检索用户从字体对话框中选择的字体。|  
|`CMFCPropertyGridFontProperty::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|`CMFCPropertyGridFontProperty::OnClickButton`|调用由结构，当用户单击属性包含的按钮。  （重写 [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)。）|  
  
## 备注  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## 要求  
 **标头:** afxpropertygridctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)