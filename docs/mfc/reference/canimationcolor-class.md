---
title: "CAnimationColor 类 | Microsoft Docs"
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
  - "CAnimationColor"
  - "afxanimationcontroller/CAnimationColor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationColor 类"
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationColor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现可对颜色的红色、绿色和蓝色分量进行动画处理的颜色功能。  
  
## 语法  
  
```  
class CAnimationColor : public CAnimationBaseObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationColor::CAnimationColor](../Topic/CAnimationColor::CAnimationColor.md)|已重载。  构造动画颜色对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationColor::AddTransition](../Topic/CAnimationColor::AddTransition.md)|为红色、绿色和蓝色分量添加转换。|  
|[CAnimationColor::GetB](../Topic/CAnimationColor::GetB.md)|提供对表示蓝色分量的 CAnimationVariable 的访问权。|  
|[CAnimationColor::GetDefaultValue](../Topic/CAnimationColor::GetDefaultValue.md)|返回颜色分量的默认值。|  
|[CAnimationColor::GetG](../Topic/CAnimationColor::GetG.md)|提供对表示绿色分量的 CAnimationVariable 的访问权。|  
|[CAnimationColor::GetR](../Topic/CAnimationColor::GetR.md)|提供对表示红色分量的 CAnimationVariable 的访问权。|  
|[CAnimationColor::GetValue](../Topic/CAnimationColor::GetValue.md)|返回当前值。|  
|[CAnimationColor::SetDefaultValue](../Topic/CAnimationColor::SetDefaultValue.md)|设置默认值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationColor::GetAnimationVariableList](../Topic/CAnimationColor::GetAnimationVariableList.md)|将封装的动画变量放入列表中。  （重写 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAnimationColor::operator COLORREF](../Topic/CAnimationColor::operator%20COLORREF.md)||  
|[CAnimationColor::operator\=](../Topic/CAnimationColor::operator=.md)|将颜色分配给 CAnimationColor。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationColor::m\_bValue](../Topic/CAnimationColor::m_bValue.md)|封装的动画变量，表示动画颜色的蓝色分量。|  
|[CAnimationColor::m\_gValue](../Topic/CAnimationColor::m_gValue.md)|封装的动画变量，表示动画颜色的绿色分量。|  
|[CAnimationColor::m\_rValue](../Topic/CAnimationColor::m_rValue.md)|封装的动画变量，表示动画颜色的红色分量。|  
  
## 备注  
 CAnimationColor 类封装三个 CAnimationVariable 对象，并可以表示应用程序中的颜色。  例如，您可以使用此类对屏幕上任何对象的颜色（如，文本颜色、背景色等）进行动画处理。  若要在应用程序中使用此类，只需实例化此类的对象，使用 CAnimationController::AddAnimationObject 将其添加到动画控制器，并为每个要应用到红色、绿色和蓝色分量的转换调用 AddTransition 即可。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationColor](../../mfc/reference/canimationcolor-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)