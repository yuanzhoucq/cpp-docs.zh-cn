---
title: "CAnimationVariable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationVariable"
  - "afxanimationcontroller/CAnimationVariable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariable 类"
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationVariable 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示动画变量。  
  
## 语法  
  
```  
class CAnimationVariable;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariable::CAnimationVariable](../Topic/CAnimationVariable::CAnimationVariable.md)|构造动画变量对象。|  
|[CAnimationVariable::~CAnimationVariable](../Topic/CAnimationVariable::~CAnimationVariable.md)|该析构函数。  当 CAnimationVariable 对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariable::AddTransition](../Topic/CAnimationVariable::AddTransition.md)|添加转换。|  
|[CAnimationVariable::ApplyTransitions](../Topic/CAnimationVariable::ApplyTransitions.md)|将该内部列表的转换添加到情节提要。|  
|[CAnimationVariable::ClearTransitions](../Topic/CAnimationVariable::ClearTransitions.md)|清除转换。|  
|[CAnimationVariable::Create](../Topic/CAnimationVariable::Create.md)|创建基础动画变量 COM 对象。|  
|[CAnimationVariable::CreateTransitions](../Topic/CAnimationVariable::CreateTransitions.md)|创建要应用于此动画变量的所有转换。|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](../Topic/CAnimationVariable::EnableIntegerValueChangedEvent.md)|启用或禁用 IntegerValueChanged 事件。|  
|[CAnimationVariable::EnableValueChangedEvent](../Topic/CAnimationVariable::EnableValueChangedEvent.md)|启用或禁用 ValueChanged 事件。|  
|[CAnimationVariable::GetDefaultValue](../Topic/CAnimationVariable::GetDefaultValue.md)|返回默认值。|  
|[CAnimationVariable::GetParentAnimationObject](../Topic/CAnimationVariable::GetParentAnimationObject.md)|返回该父级动画对象。|  
|[CAnimationVariable::GetValue](../Topic/CAnimationVariable::GetValue.md)|已重载。  返回动画变量的当前值。|  
|[CAnimationVariable::GetVariable](../Topic/CAnimationVariable::GetVariable.md)|返回指向 IUIAnimationVariable COM 对象的指针。|  
|[CAnimationVariable::SetDefaultValue](../Topic/CAnimationVariable::SetDefaultValue.md)|设置默认值，并释放 IUIAnimationVariable COM 对象。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariable::SetParentAnimationObject](../Topic/CAnimationVariable::SetParentAnimationObject.md)|设置动画变量和动画对象之间的关系。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariable::m\_bAutodestroyTransitions](../Topic/CAnimationVariable::m_bAutodestroyTransitions.md)|指定是否应删除相关的转换对象。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariable::m\_dblDefaultValue](../Topic/CAnimationVariable::m_dblDefaultValue.md)|指定传播给 IUIAnimationVariable 的默认值。|  
|[CAnimationVariable::m\_lstTransitions](../Topic/CAnimationVariable::m_lstTransitions.md)|包含对此动画变量进行动画处理的转换的列表。|  
|[CAnimationVariable::m\_pParentObject](../Topic/CAnimationVariable::m_pParentObject.md)|指向封装此动画变量的动画对象的指针。|  
|[CAnimationVariable::m\_variable](../Topic/CAnimationVariable::m_variable.md)|存储指向 IUIAnimationVariable COM 对象的指针。  如果尚未创建 COM 对象或创建失败，则为 NULL。|  
  
## 备注  
 CAnimationVariable 类封装 IUIAnimationVariable COM 对象。  它还包含要应用于情节提要中动画变量的转换的列表。  CAnimationVariable 对象被嵌入到动画对象，可以表示应用程序中经过动画处理的值、点、大小、颜色和矩形。  
  
## 继承层次结构  
 [CAnimationVariable](../../mfc/reference/canimationvariable-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)