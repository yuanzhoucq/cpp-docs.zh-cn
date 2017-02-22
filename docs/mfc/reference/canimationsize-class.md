---
title: "CAnimationSize 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationSize"
  - "CAnimationSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationSize 类"
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationSize 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现可对大小对象的维度进行动画处理的大小对象功能。  
  
## 语法  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationSize::CAnimationSize](../Topic/CAnimationSize::CAnimationSize.md)|已重载。  构造动画大小对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationSize::AddTransition](../Topic/CAnimationSize::AddTransition.md)|为宽度和高度添加转换。|  
|[CAnimationSize::GetCX](../Topic/CAnimationSize::GetCX.md)|提供对表示宽度的 CAnimationVariable 的访问权。|  
|[CAnimationSize::GetCY](../Topic/CAnimationSize::GetCY.md)|提供对表示高度的 CAnimationVariable 的访问权。|  
|[CAnimationSize::GetDefaultValue](../Topic/CAnimationSize::GetDefaultValue.md)|返回宽度和高度的默认值。|  
|[CAnimationSize::GetValue](../Topic/CAnimationSize::GetValue.md)|返回当前值。|  
|[CAnimationSize::SetDefaultValue](../Topic/CAnimationSize::SetDefaultValue.md)|设置默认值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationSize::GetAnimationVariableList](../Topic/CAnimationSize::GetAnimationVariableList.md)|将封装的动画变量放入列表中。  （重写 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAnimationSize::operator CSize](../Topic/CAnimationSize::operator%20CSize.md)|将 CAnimationSize 转换为 CSize。|  
|[CAnimationSize::operator\=](../Topic/CAnimationSize::operator=.md)|将 szSrc 分配给 CAnimationSize。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationSize::m\_cxValue](../Topic/CAnimationSize::m_cxValue.md)|封装的动画变量，表示动画大小的宽度。|  
|[CAnimationSize::m\_cyValue](../Topic/CAnimationSize::m_cyValue.md)|封装的动画变量，表示动画大小的高度。|  
  
## 备注  
 CAnimationSize 类封装两个 CAnimationVariable 对象，并可以表示应用程序中的大小。  例如，您可以使用此类对屏幕上任何二维对象的大小（如，矩形、控件等）进行动画处理。  若要在应用程序中使用此类，只需实例化此类的对象，使用 CAnimationController::AddAnimationObject 将其添加到动画控制器，并为每个要应用到宽度和\/或高度的转换调用 AddTransition 即可。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationSize](../../mfc/reference/canimationsize-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)