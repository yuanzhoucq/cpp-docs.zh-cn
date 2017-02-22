---
title: "CAnimationBaseObject 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationBaseObject"
  - "CAnimationBaseObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationBaseObject 类"
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationBaseObject 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有动画对象的基类。  
  
## 语法  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationBaseObject::CAnimationBaseObject](../Topic/CAnimationBaseObject::CAnimationBaseObject.md)|已重载。  构造动画对象。|  
|[CAnimationBaseObject::~CAnimationBaseObject](../Topic/CAnimationBaseObject::~CAnimationBaseObject.md)|该析构函数。  当动画对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationBaseObject::ApplyTransitions](../Topic/CAnimationBaseObject::ApplyTransitions.md)|将转换添加到具有封装的动画变量的情节提要。|  
|[CAnimationBaseObject::ClearTransitions](../Topic/CAnimationBaseObject::ClearTransitions.md)|删除所有相关的转换。|  
|[CAnimationBaseObject::ContainsVariable](../Topic/CAnimationBaseObject::ContainsVariable.md)|确定动画对象是否包含特定的动画变量。|  
|[CAnimationBaseObject::CreateTransitions](../Topic/CAnimationBaseObject::CreateTransitions.md)|创建与动画对象关联的转换。|  
|[CAnimationBaseObject::DetachFromController](../Topic/CAnimationBaseObject::DetachFromController.md)|从父级动画控制器中分离动画对象。|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](../Topic/CAnimationBaseObject::EnableIntegerValueChangedEvent.md)|设置整数值已更改事件处理程序。|  
|[CAnimationBaseObject::EnableValueChangedEvent](../Topic/CAnimationBaseObject::EnableValueChangedEvent.md)|设置值已更改事件处理程序。|  
|[CAnimationBaseObject::GetAutodestroyTransitions](../Topic/CAnimationBaseObject::GetAutodestroyTransitions.md)|指示是否应自动销毁相关的转换。|  
|[CAnimationBaseObject::GetGroupID](../Topic/CAnimationBaseObject::GetGroupID.md)|返回当前组 ID。|  
|[CAnimationBaseObject::GetObjectID](../Topic/CAnimationBaseObject::GetObjectID.md)|返回当前对象 ID。|  
|[CAnimationBaseObject::GetUserData](../Topic/CAnimationBaseObject::GetUserData.md)|返回用户定义的数据。|  
|[CAnimationBaseObject::SetAutodestroyTransitions](../Topic/CAnimationBaseObject::SetAutodestroyTransitions.md)|设置可指示自动销毁转换的标志。|  
|[CAnimationBaseObject::SetID](../Topic/CAnimationBaseObject::SetID.md)|设置新的 ID。|  
|[CAnimationBaseObject::SetUserData](../Topic/CAnimationBaseObject::SetUserData.md)|设置用户定义的数据。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)|收集指向包含的动画变量的指针。|  
|[CAnimationBaseObject::SetParentAnimationObjects](../Topic/CAnimationBaseObject::SetParentAnimationObjects.md)|建立包含在动画对象及其容器中的动画变量之间的关系。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationBaseObject::m\_bAutodestroyTransitions](../Topic/CAnimationBaseObject::m_bAutodestroyTransitions.md)|指定是否应自动销毁相关的转换。|  
|[CAnimationBaseObject::m\_dwUserData](../Topic/CAnimationBaseObject::m_dwUserData.md)|存储用户定义的数据。|  
|[CAnimationBaseObject::m\_nGroupID](../Topic/CAnimationBaseObject::m_nGroupID.md)|指定该动画对象的组 ID。|  
|[CAnimationBaseObject::m\_nObjectID](../Topic/CAnimationBaseObject::m_nObjectID.md)|指定该动画对象的对象 ID。|  
|[CAnimationBaseObject::m\_pParentController](../Topic/CAnimationBaseObject::m_pParentController.md)|指向该父级动画控制器的指针。|  
  
## 备注  
 此类实现用于所有动画对象的基本方法。  动画对象可以表示应用程序中的值、点、大小、矩形或颜色，也可以表示任何自定义实体。  动画对象存储在动画组中（参见 CAnimationGroup）。  可以分别对每个组进行动画处理，并可将其视为模拟情节提要。  动画对象可封装一个或多个动画变量（请参见 CAnimationVariable），取决于它的逻辑表示形式。  例如，CAnimationRect 包含四个动画变量 \- 一个变量用于矩形的一条边。  每个动画对象类会公开重载的 AddTransition 方法，应将该方法用来将转换应用于封装的动画变量。  动画对象可通过对象 ID（可选）和组 ID 进行标识。  要将动画对象放置到正确的组，必需要有组 ID，但如果未指定组 ID，则对象会被放置在 ID 为 0 的默认组中。  如果您使用不同的 GroupID 来调用 SetID，则动画对象会被移动到另一个组（如有需要，会创建新的组）。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)