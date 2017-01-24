---
title: "CSinusoidalTransitionFromRange 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CSinusoidalTransitionFromRange"
  - "CSinusoidalTransitionFromRange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSinusoidalTransitionFromRange 类"
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSinusoidalTransitionFromRange 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装具有给定振动范围的正弦范围转换。  
  
## 语法  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](../Topic/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange.md)|构造转换对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSinusoidalTransitionFromRange::Create](../Topic/CSinusoidalTransitionFromRange::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CSinusoidalTransitionFromRange::m\_dblMaximumValue](../Topic/CSinusoidalTransitionFromRange::m_dblMaximumValue.md)|该动画变量在正弦波波峰的值。|  
|[CSinusoidalTransitionFromRange::m\_dblMinimumValue](../Topic/CSinusoidalTransitionFromRange::m_dblMinimumValue.md)|该动画变量在正弦波波谷的值。|  
|[CSinusoidalTransitionFromRange::m\_duration](../Topic/CSinusoidalTransitionFromRange::m_duration.md)|转换的持续时间。|  
|[CSinusoidalTransitionFromRange::m\_period](../Topic/CSinusoidalTransitionFromRange::m_period.md)|正弦波的振动周期（以秒为单位）。|  
|[CSinusoidalTransitionFromRange::m\_slope](../Topic/CSinusoidalTransitionFromRange::m_slope.md)|改转换的开头的斜率。|  
  
## 备注  
 在整个正弦\-范围转换期间，动画变量的值会在指定的最小值和最大值之间波动。  该斜率参数用于消除由其他参数指定的两个正弦波之间可能产生的歧义。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)