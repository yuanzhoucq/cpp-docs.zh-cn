---
title: "CLinearTransitionFromSpeed 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CLinearTransitionFromSpeed"
  - "CLinearTransitionFromSpeed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinearTransitionFromSpeed 类"
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLinearTransitionFromSpeed 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装线性速度转换。  
  
## 语法  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](../Topic/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed.md)|构造线性速度转换对象，并初始化其速度和最终值。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CLinearTransitionFromSpeed::Create](../Topic/CLinearTransitionFromSpeed::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CLinearTransitionFromSpeed::m\_dblFinalValue](../Topic/CLinearTransitionFromSpeed::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
|[CLinearTransitionFromSpeed::m\_dblSpeed](../Topic/CLinearTransitionFromSpeed::m_dblSpeed.md)|该变量速度的绝对值。|  
  
## 备注  
 在线性速度转换期间，动画变量的值会以指定的速率更改。  转换的持续时间由初始值与指定的最终值之间的差来确定。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)