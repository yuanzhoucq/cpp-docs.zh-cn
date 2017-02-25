---
title: "CCubicTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCubicTransition"
  - "afxanimationcontroller/CCubicTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCubicTransition 类"
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CCubicTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装立方转换。  
  
## 语法  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCubicTransition::CCubicTransition](../Topic/CCubicTransition::CCubicTransition.md)|构造转换对象，并初始化其参数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCubicTransition::Create](../Topic/CCubicTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCubicTransition::m\_dblFinalValue](../Topic/CCubicTransition::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
|[CCubicTransition::m\_dblFinalVelocity](../Topic/CCubicTransition::m_dblFinalVelocity.md)|该变量在此转换结束时的速度。|  
|[CCubicTransition::m\_duration](../Topic/CCubicTransition::m_duration.md)|转换的持续时间。|  
  
## 备注  
 在三次转换期间，动画变量的值会在该转换的持续时间内从其初始值更改为指定的最终值，并以指定的速度结束。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CCubicTransition](../../mfc/reference/ccubictransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)