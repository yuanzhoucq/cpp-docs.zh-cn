---
title: "CDiscreteTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDiscreteTransition"
  - "afxanimationcontroller/CDiscreteTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDiscreteTransition 类"
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CDiscreteTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装离散转换。  
  
## 语法  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDiscreteTransition::CDiscreteTransition](../Topic/CDiscreteTransition::CDiscreteTransition.md)|构造离散转换对象，并初始化其参数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDiscreteTransition::Create](../Topic/CDiscreteTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDiscreteTransition::m\_dblFinalValue](../Topic/CDiscreteTransition::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
|[CDiscreteTransition::m\_delay](../Topic/CDiscreteTransition::m_delay.md)|将瞬时切换延迟到最终值的时间。|  
|[CDiscreteTransition::m\_hold](../Topic/CDiscreteTransition::m_hold.md)|将该变量保持为最终值的时间。|  
  
## 备注  
 在离散转换期间，动画变量会在指定的延迟时间内保持为初始值，然后瞬时切换为指定的最终值，并在给定的保留时间内保持为该值。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)