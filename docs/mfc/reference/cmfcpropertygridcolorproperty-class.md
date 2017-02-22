---
title: "CMFCPropertyGridColorProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridColorProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridColorProperty class"
  - "CMFCPropertyGridColorProperty::FormatProperty method"
  - "CMFCPropertyGridColorProperty::OnClickButton method"
  - "CMFCPropertyGridColorProperty::OnDrawValue method"
  - "CMFCPropertyGridColorProperty::OnEdit method"
  - "CMFCPropertyGridColorProperty::OnUpdateValue method"
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCPropertyGridColorProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyGridColorProperty` 类支持用于打开颜色选择对话框的属性列表控件项。  
  
## 语法  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](../Topic/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty.md)|构造 `CMFCPropertyGridColorProperty` 对象。|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](../Topic/CMFCPropertyGridColorProperty::EnableAutomaticButton.md)|启用颜色选择对话框上的*“自动”*按钮。  （标准的“自动”按钮标记为**“自动”**。）|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](../Topic/CMFCPropertyGridColorProperty::EnableOtherButton.md)|启用颜色选择对话框上的*“其他”*按钮。  （标准的“其他”按钮标记为**“更多颜色…”**。）|  
|`CMFCPropertyGridColorProperty::FormatProperty`|设置属性值的文本表示形式的格式。  （替代 [CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md)。）|  
|[CMFCPropertyGridColorProperty::GetColor](../Topic/CMFCPropertyGridColorProperty::GetColor.md)|获取属性的当前颜色。|  
|`CMFCPropertyGridColorProperty::GetThisClass`|由框架用于获取指向与此类类型关联的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象的指针。|  
|`CMFCPropertyGridColorProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。  （替代 [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)。）|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|由框架调用以显示属性值。  （替代 [CMFCPropertyGridProperty::OnDrawValue](../Topic/CMFCPropertyGridProperty::OnDrawValue.md)。）|  
|`CMFCPropertyGridColorProperty::OnEdit`|当用户要修改属性值时由框架调用。  （替代 [CMFCPropertyGridProperty::OnEdit](../Topic/CMFCPropertyGridProperty::OnEdit.md)。）|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|当可编辑属性值已更改时由框架调用。  （替代 [CMFCPropertyGridProperty::OnUpdateValue](../Topic/CMFCPropertyGridProperty::OnUpdateValue.md)。）|  
|[CMFCPropertyGridColorProperty::SetColor](../Topic/CMFCPropertyGridColorProperty::SetColor.md)|设置属性的新颜色。|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](../Topic/CMFCPropertyGridColorProperty::SetColumnsNumber.md)|指定当前颜色属性网格中的列数。|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](../Topic/CMFCPropertyGridColorProperty::SetOriginalValue.md)|设置可编辑属性的原始值。|  
  
## 备注  
 `CMFCPropertyGridColorProperty` 类支持可添加到属性列表控件的颜色属性。  有关详细信息，请参阅 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)。  
  
## 示例  
 下面的示例演示如何构造 `CMFCPropertyGridColorProperty` 类的对象，以及如何使用 `CMFCPropertyGridColorProperty` 类的各种方法来配置此对象。  下面的代码介绍如何启用“自动”按钮和“其他”按钮，以及如何设置颜色和列数。  本示例是[新控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/CPP/cmfcpropertygridcolorproperty-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## 要求  
 **标头：**afxpropertygridctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)