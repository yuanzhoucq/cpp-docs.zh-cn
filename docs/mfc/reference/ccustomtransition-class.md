---
title: "CCustomTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CCustomTransition"
  - "CCustomTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCustomTransition 类"
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CCustomTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现自定义转换。  
  
## 语法  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCustomTransition::CCustomTransition](../Topic/CCustomTransition::CCustomTransition.md)|构造自定义转换对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCustomTransition::Create](../Topic/CCustomTransition::Create.md)|调用转换库以创建封装的转换 COM 对象。  （重写 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)。）|  
|[CCustomTransition::SetInitialValue](../Topic/CCustomTransition::SetInitialValue.md)|设置初始值，该值将应用于与此转换关联的动画变量。|  
|[CCustomTransition::SetInitialVelocity](../Topic/CCustomTransition::SetInitialVelocity.md)|设置初始速度，该值将应用于与此转换关联的动画变量。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCustomTransition::m\_bInitialValueSpecified](../Topic/CCustomTransition::m_bInitialValueSpecified.md)|指定初始值是否已使用 SetInitialValue 指定。|  
|[CCustomTransition::m\_bInitialVelocitySpecified](../Topic/CCustomTransition::m_bInitialVelocitySpecified.md)|指定初始速度是否已使用 SetInitialVelocity 指定。|  
|[CCustomTransition::m\_initialValue](../Topic/CCustomTransition::m_initialValue.md)|存储初始值。|  
|[CCustomTransition::m\_initialVelocity](../Topic/CCustomTransition::m_initialVelocity.md)|存储初始速度。|  
|[CCustomTransition::m\_pInterpolator](../Topic/CCustomTransition::m_pInterpolator.md)|存储指向自定义内插器的指针。|  
  
## 备注  
 使用 CCustomTransitions 类，开发人员可以实现自定义转换。  它被作为标准的转换进行创建和使用，但它的构造函数接受作为参数的指向自定义内插器的指针。  执行以下步骤以使用自定义转换：1.  从 CCustomInterpolator 派生类，并至少实施 InterpolateValue 方法。  2.  确保自定义内插程序对象的生存期必须长于动画所使用的持续时间。  3.  实例化（使用运算符 new）CCustomTransition 对象，并传递指向构造函数中自定义内插器的指针。  4.  如果自定义内插需要这些参数，则调用 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity。  5.  将指向自定义转换的指针传递给动画对象的 AddTransition 方法，该动画对象的值应使用自定义算法进行动画处理。  6.  当动画对象的值更改时，Windows 动画 API 将调用 CCustomInterpolator 中的 InterpolateValue（以及其他相关的方法）。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CCustomTransition](../../mfc/reference/ccustomtransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)