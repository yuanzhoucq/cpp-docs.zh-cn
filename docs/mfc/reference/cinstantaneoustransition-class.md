---
title: "CInstantaneousTransition 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CInstantaneousTransition"
  - "CInstantaneousTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInstantaneousTransition 类"
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInstantaneousTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装瞬时转换。  
  
## 语法  
  
```  
class CInstantaneousTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInstantaneousTransition::CInstantaneousTransition](../Topic/CInstantaneousTransition::CInstantaneousTransition.md)|构造转换对象，并初始化其最终值。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CInstantaneousTransition::Create](../Topic/CInstantaneousTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CInstantaneousTransition::m\_dblFinalValue](../Topic/CInstantaneousTransition::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
  
## 备注  
 在瞬时转换期间，动画变量的值会从其当前值瞬时转换到指定的最终值。  此转换的持续时间始终为零。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)