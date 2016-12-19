---
title: "CMFCPropertyGridFileProperty Class | Microsoft Docs"
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
  - "CMFCPropertyGridFileProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridFileProperty class"
  - "CMFCPropertyGridFileProperty::OnClickButton method"
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridFileProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyGridFileProperty` 选件类支持属性中打开文件选择对话框的控件项目。  
  
## 语法  
  
```  
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](../Topic/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty.md)|构造 `CMFCPropertyGridFileProperty` 对象。|  
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCPropertyGridFileProperty::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|`CMFCPropertyGridFileProperty::OnClickButton`|（重写 [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)。）|  
  
### 备注  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## 要求  
 **标头:** afxpropertygridctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)