---
title: "CReversalTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CReversalTransition"
  - "CReversalTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReversalTransition 类"
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CReversalTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装反向转换。  
  
## 语法  
  
```  
class CReversalTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CReversalTransition::CReversalTransition](../Topic/CReversalTransition::CReversalTransition.md)|构造反向转换对象，并初始化其持续时间。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CReversalTransition::Create](../Topic/CReversalTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CReversalTransition::m\_duration](../Topic/CReversalTransition::m_duration.md)|转换的持续时间。|  
  
## 备注  
 反向转换会以平稳的方式在给定的持续时间内更改方向。  最终值将与初始值相同，并且最终速度将为负值的初始速度。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CReversalTransition](../../mfc/reference/creversaltransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)