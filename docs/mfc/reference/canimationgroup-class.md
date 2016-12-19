---
title: "CAnimationGroup 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationGroup"
  - "CAnimationGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationGroup 类"
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationGroup 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现动画组，它组合动画演示图板、动画对象和转换来定义动画。  
  
## 语法  
  
```  
class CAnimationGroup;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationGroup::CAnimationGroup](../Topic/CAnimationGroup::CAnimationGroup.md)|构造动画组。|  
|[CAnimationGroup::~CAnimationGroup](../Topic/CAnimationGroup::~CAnimationGroup.md)|该析构函数。  当动画组被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationGroup::Animate](../Topic/CAnimationGroup::Animate.md)|对组进行动画处理。|  
|[CAnimationGroup::ApplyTransitions](../Topic/CAnimationGroup::ApplyTransitions.md)|将转换应用于动画对象。|  
|[CAnimationGroup::FindAnimationObject](../Topic/CAnimationGroup::FindAnimationObject.md)|查找包含指定的动画变量的动画对象。|  
|[CAnimationGroup::GetGroupID](../Topic/CAnimationGroup::GetGroupID.md)|返回 GroupID。|  
|[CAnimationGroup::RemoveKeyframes](../Topic/CAnimationGroup::RemoveKeyframes.md)|删除并有选择地销毁属于动画组的所有关键帧。|  
|[CAnimationGroup::RemoveTransitions](../Topic/CAnimationGroup::RemoveTransitions.md)|从属于动画组的动画对象中删除转换。|  
|[CAnimationGroup::Schedule](../Topic/CAnimationGroup::Schedule.md)|将动画安排在指定的时间。|  
|[CAnimationGroup::SetAutodestroyTransitions](../Topic/CAnimationGroup::SetAutodestroyTransitions.md)|指引属于组的所有动画对象自动销毁转换。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationGroup::AddKeyframes](../Topic/CAnimationGroup::AddKeyframes.md)|将关键帧添加到情节提要的帮助器。|  
|[CAnimationGroup::AddTransitions](../Topic/CAnimationGroup::AddTransitions.md)|将转换添加到情节提要的帮助器。|  
|[CAnimationGroup::CreateTransitions](../Topic/CAnimationGroup::CreateTransitions.md)|创建 COM 转换对象的帮助器。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationGroup::m\_bAutoclearTransitions](../Topic/CAnimationGroup::m_bAutoclearTransitions.md)|指定如何从属于组的动画对象中清除过渡。  如果此成员为 TRUE，则当动画已经安排好时，会自动删除转换。  否则，您需要手动删除转换。|  
|[CAnimationGroup::m\_bAutodestroyAnimationObjects](../Topic/CAnimationGroup::m_bAutodestroyAnimationObjects.md)|指定如何销毁动画对象。  如果此参数为 TRUE，则动画对象将在该组被销毁时自动销毁。  否则，必须手动销毁动画对象。  默认值为 FALSE。  仅当属于组的所有动画对象使用运算符 new 进行动态分配时，将此值设置为 TRUE。|  
|[CAnimationGroup::m\_bAutodestroyKeyframes](../Topic/CAnimationGroup::m_bAutodestroyKeyframes.md)|指定如何销毁关键帧。  如果此值为 TRUE，则会删除并销毁所有关键帧；否则只是从列表中将其删除。  默认值为 TRUE。|  
|[CAnimationGroup::m\_lstAnimationObjects](../Topic/CAnimationGroup::m_lstAnimationObjects.md)|包含动画对象列表。|  
|[CAnimationGroup::m\_lstKeyFrames](../Topic/CAnimationGroup::m_lstKeyFrames.md)|包含关键帧列表。|  
|[CAnimationGroup::m\_pStoryboard](../Topic/CAnimationGroup::m_pStoryboard.md)|到动画情节提要的点。  只有在调用动画之后，此指针才有效。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationGroup::m\_nGroupID](../Topic/CAnimationGroup::m_nGroupID.md)|动画组的唯一标识符。|  
|[CAnimationGroup::m\_pParentController](../Topic/CAnimationGroup::m_pParentController.md)|指向此组所属的动画控制器的指针。|  
  
## 备注  
 当您使用 CAnimationController::AddAnimationObject 添加动画对象时，动画控制器 \(CAnimationController\) 会自动创建动画组。  动画组使用 GroupID 来标识，通常用作操作动画组的参数。  取自正添加到新动画组的第一个动画对象的 GroupID。  封装的动画情节提要可在您调用 CAnimationController::AnimateGroup 之后创建，并可通过公共成员 m\_pStoryboard 进行访问。  
  
## 继承层次结构  
 [CAnimationGroup](../../mfc/reference/canimationgroup-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)