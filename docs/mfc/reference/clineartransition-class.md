---
title: "CLinearTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CLinearTransition"
  - "afxanimationcontroller/CLinearTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinearTransition 类"
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CLinearTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装线性转换。  
  
## 语法  
  
```  
class CLinearTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CLinearTransition::CLinearTransition](../Topic/CLinearTransition::CLinearTransition.md)|构造线性转换对象，并初始化其持续时间和最终值。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CLinearTransition::Create](../Topic/CLinearTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CLinearTransition::m\_dblFinalValue](../Topic/CLinearTransition::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
|[CLinearTransition::m\_duration](../Topic/CLinearTransition::m_duration.md)|转换的持续时间。|  
  
## 备注  
 在线性转换期间，动画变量的值会从其初始值线性转换为指定的最终值。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransition](../../mfc/reference/clineartransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)