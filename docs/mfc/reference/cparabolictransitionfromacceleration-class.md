---
title: "CParabolicTransitionFromAcceleration 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CParabolicTransitionFromAcceleration"
  - "CParabolicTransitionFromAcceleration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CParabolicTransitionFromAcceleration 类"
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CParabolicTransitionFromAcceleration 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装抛物线加速转换。  
  
## 语法  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](../Topic/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration.md)|构造抛物线加速转换，并使用指定的参数对其进行初始化。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CParabolicTransitionFromAcceleration::Create](../Topic/CParabolicTransitionFromAcceleration::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CParabolicTransitionFromAcceleration::m\_dblAcceleration](../Topic/CParabolicTransitionFromAcceleration::m_dblAcceleration.md)|转换期间该动画变量的加速度。|  
|[CParabolicTransitionFromAcceleration::m\_dblFinalValue](../Topic/CParabolicTransitionFromAcceleration::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
|[CParabolicTransitionFromAcceleration::m\_dblFinalVelocity](../Topic/CParabolicTransitionFromAcceleration::m_dblFinalVelocity.md)|该动画变量在过渡结束时的速度。|  
  
## 备注  
 在抛物线\-加速转换期间，动画变量的值会从其初始值更改为指定的最终值，并以指定的速度结束。  您可以通过指定加速速率来控制该变量如何快速达到最终值。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)