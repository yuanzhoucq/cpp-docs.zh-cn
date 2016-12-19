---
title: "CCustomInterpolator 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CCustomInterpolator"
  - "CCustomInterpolator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCustomInterpolator 类"
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCustomInterpolator 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现基本插值程序。  
  
## 语法  
  
```  
class CCustomInterpolator;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCustomInterpolator::CCustomInterpolator](../Topic/CCustomInterpolator::CCustomInterpolator.md)|已重载。  构造自定义内插器对象，并将持续时间和速度初始化为指定的值。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCustomInterpolator::GetDependencies](../Topic/CCustomInterpolator::GetDependencies.md)|获取该内插器的依赖项。|  
|[CCustomInterpolator::GetDuration](../Topic/CCustomInterpolator::GetDuration.md)|获取该内插器的持续时间。|  
|[CCustomInterpolator::GetFinalValue](../Topic/CCustomInterpolator::GetFinalValue.md)|获取由该内插器产生的最终值。|  
|[CCustomInterpolator::Init](../Topic/CCustomInterpolator::Init.md)|初始化持续时间和最终值。|  
|[CCustomInterpolator::InterpolateValue](../Topic/CCustomInterpolator::InterpolateValue.md)|在给定的偏移位置内插该值。|  
|[CCustomInterpolator::InterpolateVelocity](../Topic/CCustomInterpolator::InterpolateVelocity.md)|在给定的偏移位置内插该速度|  
|[CCustomInterpolator::SetDuration](../Topic/CCustomInterpolator::SetDuration.md)|设置该内插器的持续时间。|  
|[CCustomInterpolator::SetInitialValueAndVelocity](../Topic/CCustomInterpolator::SetInitialValueAndVelocity.md)|设置内插器的初始值和速度。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCustomInterpolator::m\_currentValue](../Topic/CCustomInterpolator::m_currentValue.md)|内插的值。|  
|[CCustomInterpolator::m\_currentVelocity](../Topic/CCustomInterpolator::m_currentVelocity.md)|内插的速度。|  
|[CCustomInterpolator::m\_duration](../Topic/CCustomInterpolator::m_duration.md)|转换的持续时间。|  
|[CCustomInterpolator::m\_finalValue](../Topic/CCustomInterpolator::m_finalValue.md)|变量在该转换结尾的速度。|  
|[CCustomInterpolator::m\_initialValue](../Topic/CCustomInterpolator::m_initialValue.md)|该动画变量在此转换开头的值。|  
|[CCustomInterpolator::m\_initialVelocity](../Topic/CCustomInterpolator::m_initialVelocity.md)|该变量在此转换开头的速度。|  
  
## 备注  
 从 CCustomInterpolator 派生一个类，并重写所有必需的方法以实现自定义内插算法。  应将指向此类的指针作为参数传递给 CCustomTransition。  
  
## 继承层次结构  
 [CCustomInterpolator](../../mfc/reference/ccustominterpolator-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)