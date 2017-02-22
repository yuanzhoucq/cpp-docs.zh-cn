---
title: "CAnimationPoint 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationPoint"
  - "afxanimationcontroller/CAnimationPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationPoint 类"
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationPoint 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现可对点坐标进行动画处理的点功能。  
  
## 语法  
  
```  
class CAnimationPoint : public CAnimationBaseObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationPoint::CAnimationPoint](../Topic/CAnimationPoint::CAnimationPoint.md)|已重载。  构造 CAnimationPoint 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationPoint::AddTransition](../Topic/CAnimationPoint::AddTransition.md)|为 X 和 Y 坐标添加转换。|  
|[CAnimationPoint::GetDefaultValue](../Topic/CAnimationPoint::GetDefaultValue.md)|返回 X 和 Y 坐标的默认值。|  
|[CAnimationPoint::GetValue](../Topic/CAnimationPoint::GetValue.md)|返回当前值。|  
|[CAnimationPoint::GetX](../Topic/CAnimationPoint::GetX.md)|提供对 X 坐标的 CAnimationVariable 的访问权。|  
|[CAnimationPoint::GetY](../Topic/CAnimationPoint::GetY.md)|提供对 Y 坐标的 CAnimationVariable 的访问权。|  
|[CAnimationPoint::SetDefaultValue](../Topic/CAnimationPoint::SetDefaultValue.md)|设置默认值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationPoint::GetAnimationVariableList](../Topic/CAnimationPoint::GetAnimationVariableList.md)|将封装的动画变量放入列表中。  （重写 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAnimationPoint::operator CPoint](../Topic/CAnimationPoint::operator%20CPoint.md)|将 CAnimationPoint 转换为 CPoint。|  
|[CAnimationPoint::operator\=](../Topic/CAnimationPoint::operator=.md)|将 ptSrc 分配给 CAnimationPoint。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationPoint::m\_xValue](../Topic/CAnimationPoint::m_xValue.md)|封装的动画变量，表示动画点的 X 坐标。|  
|[CAnimationPoint::m\_yValue](../Topic/CAnimationPoint::m_yValue.md)|封装的动画变量，表示动画点的 Y 坐标。|  
  
## 备注  
 CAnimationPoint 类封装两个 CAnimationVariable 对象，并可以表示应用程序中的点。  例如，您可以使用此类对屏幕上任何对象的位置（如，文本字符串、圆、点等）进行动画处理。  若要在应用程序中使用此类，只需实例化此类的对象，使用 CAnimationController::AddAnimationObject 将其添加到动画控制器，并为每个要应用到 X 和 Y 坐标的转换调用 AddTransition 即可。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationPoint](../../mfc/reference/canimationpoint-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)