---
title: "CSmoothStopTransition 类 | Microsoft Docs"
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
  - "CSmoothStopTransition"
  - "afxanimationcontroller/CSmoothStopTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSmoothStopTransition 类"
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSmoothStopTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装平稳停止转换。  
  
## 语法  
  
```  
class CSmoothStopTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSmoothStopTransition::CSmoothStopTransition](../Topic/CSmoothStopTransition::CSmoothStopTransition.md)|构造平滑\-停止转换对象，并初始化其最大持续时间和最终值。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSmoothStopTransition::Create](../Topic/CSmoothStopTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CSmoothStopTransition::m\_dblFinalValue](../Topic/CSmoothStopTransition::m_dblFinalValue.md)|该动画变量在此转换结尾的值。|  
|[CSmoothStopTransition::m\_maximumDuration](../Topic/CSmoothStopTransition::m_maximumDuration.md)|该转换的最大持续时间。|  
  
## 备注  
 当平滑\-停止转换接近给定的最终值时，转换会减速，然后在速度为零时到达该值。  转换的持续时间由初始速度、初始值与最终值之间的差以及指定的最大持续时间来确定。  如果没有解决方案包含单一抛物线圆弧，则此方法创将建三次方转换。  因为所有的转换会自动清除，所以建议使用运算符 new 对其进行分配。  封装的 IUIAnimationTransition COM 对象由 CAnimationController::AnimateGroup 创建，然后直到其为 NULL。  在创建此 COM 对象后更改成员变量不起任何作用。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)