---
title: "CAnimationValue 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationValue"
  - "CAnimationValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationValue 类"
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationValue 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现有一个值的动画对象功能。  
  
## 语法  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationValue::CAnimationValue](../Topic/CAnimationValue::CAnimationValue.md)|已重载。  构造 CAnimationValue 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationValue::AddTransition](../Topic/CAnimationValue::AddTransition.md)|添加要应用于值的转换。|  
|[CAnimationValue::GetValue](../Topic/CAnimationValue::GetValue.md)|已重载。  检索当前值。|  
|[CAnimationValue::GetVariable](../Topic/CAnimationValue::GetVariable.md)|提供对封装动画变量的访问权。|  
|[CAnimationValue::SetDefaultValue](../Topic/CAnimationValue::SetDefaultValue.md)|设置默认值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationValue::GetAnimationVariableList](../Topic/CAnimationValue::GetAnimationVariableList.md)|将封装的动画变量放入列表中。  （重写 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAnimationValue::operator DOUBLE](../Topic/CAnimationValue::operator%20DOUBLE.md)|提供 CAnimationValue 和 DOUBLE 之间的转换。|  
|[CAnimationValue::operator INT32](../Topic/CAnimationValue::operator%20INT32.md)|提供 CAnimationValue 和 INT32 之间的转换。|  
|[CAnimationValue::operator\=](../Topic/CAnimationValue::operator=.md)|已重载。  将 INT32 值分配给 CAnimationValue。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationValue::m\_value](../Topic/CAnimationValue::m_value.md)|封装的动画变量，表示动画值。|  
  
## 备注  
 CAnimationValue 类封装一个 CAnimationVariable 对象，并可以表示应用程序中的一个经动画处理的值。  例如，您可以将此类用于动画的透明度（淡入淡出效果）、角度（用来旋转对象）或用于其他需要的情况，如创建动画（取决于单个经动画处理的值）。  若要在应用程序中使用此类，只需实例化此类的对象，使用 CAnimationController::AddAnimationObject 将其添加到动画控制器，并为每个要应用到该值的转换调用 AddTransition 即可。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationValue](../../mfc/reference/canimationvalue-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)