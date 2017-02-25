---
title: "CConstantTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CConstantTransition"
  - "CConstantTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConstantTransition 类"
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CConstantTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装常量转换。  
  
## 语法  
  
```  
class CConstantTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CConstantTransition::CConstantTransition](../Topic/CConstantTransition::CConstantTransition.md)|构造转换对象，并初始化其持续时间。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CConstantTransition::Create](../Topic/CConstantTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CConstantTransition::m\_duration](../Topic/CConstantTransition::m_duration.md)|转换的持续时间。|  
  
## 备注  
 在持续转换期间，动画变量的值在该转换的持续时间内保持为初始值。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CConstantTransition](../../mfc/reference/cconstanttransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)