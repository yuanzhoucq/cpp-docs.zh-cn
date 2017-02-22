---
title: "CAnimationRect 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationRect"
  - "afxanimationcontroller/CAnimationRect"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationRect 类"
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationRect 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现可对矩形边进行动画处理的矩形功能。  
  
## 语法  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationRect::CAnimationRect](../Topic/CAnimationRect::CAnimationRect.md)|已重载。  构造动画矩形对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationRect::AddTransition](../Topic/CAnimationRect::AddTransition.md)|为左边、顶边、右边和底边坐标添加转换。|  
|[CAnimationRect::GetBottom](../Topic/CAnimationRect::GetBottom.md)|提供对表示底边坐标的 CAnimationVariable 的访问权。|  
|[CAnimationRect::GetDefaultValue](../Topic/CAnimationRect::GetDefaultValue.md)|返回矩形边界的默认值。|  
|[CAnimationRect::GetLeft](../Topic/CAnimationRect::GetLeft.md)|提供对表示左边坐标的 CAnimationVariable 的访问权。|  
|[CAnimationRect::GetRight](../Topic/CAnimationRect::GetRight.md)|提供对表示右边坐标的 CAnimationVariable 的访问权。|  
|[CAnimationRect::GetTop](../Topic/CAnimationRect::GetTop.md)|提供对表示顶边坐标的 CAnimationVariable 的访问权。|  
|[CAnimationRect::GetValue](../Topic/CAnimationRect::GetValue.md)|返回当前值。|  
|[CAnimationRect::SetDefaultValue](../Topic/CAnimationRect::SetDefaultValue.md)|设置默认值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationRect::GetAnimationVariableList](../Topic/CAnimationRect::GetAnimationVariableList.md)|将封装的动画变量放入列表中。  （重写 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAnimationRect::operator RECT](../Topic/CAnimationRect::operator%20RECT.md)|将 CAnimationRect 转换为 RECT。|  
|[CAnimationRect::operator\=](../Topic/CAnimationRect::operator=.md)|将矩形分配给 CAnimationRect。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationRect::m\_bFixedSize](../Topic/CAnimationRect::m_bFixedSize.md)|指定该矩形是否具有固定的大小。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationRect::m\_bottomValue](../Topic/CAnimationRect::m_bottomValue.md)|封装的动画变量，表示动画矩形的底边边界。|  
|[CAnimationRect::m\_leftValue](../Topic/CAnimationRect::m_leftValue.md)|封装的动画变量，表示动画矩形的左边边界。|  
|[CAnimationRect::m\_rightValue](../Topic/CAnimationRect::m_rightValue.md)|封装的动画变量，表示动画矩形的右边边界。|  
|[CAnimationRect::m\_szInitial](../Topic/CAnimationRect::m_szInitial.md)|指定动画矩形的初始大小。|  
|[CAnimationRect::m\_topValue](../Topic/CAnimationRect::m_topValue.md)|封装的动画变量，表示动画矩形的顶边边界。|  
  
## 备注  
 CAnimationRect 类封装四个 CAnimationVariable 对象，并可以表示应用程序中的矩形。  若要在应用程序中使用此类，只需实例化此类的对象，使用 CAnimationController::AddAnimationObject 将其添加到动画控制器，并为每个要应用到左边、右边、上边和下边坐标的转换调用 AddTransition 即可。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationRect](../../mfc/reference/canimationrect-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)