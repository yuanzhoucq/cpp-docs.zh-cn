---
title: "CInterpolatorBase 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CInterpolatorBase"
  - "CInterpolatorBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterpolatorBase 类"
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterpolatorBase 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现回调，它在必须计算动画变量的新值时由动画 API 调用。  
  
## 语法  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInterpolatorBase::CInterpolatorBase](../Topic/CInterpolatorBase::CInterpolatorBase.md)|构造 `CInterpolatorBase` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CInterpolatorBase::CreateInstance](../Topic/CInterpolatorBase::CreateInstance.md)|创建 `CInterpolatorBase` 实例并存储指向自定义重项，操作事件。|  
|[CInterpolatorBase::GetDependencies](../Topic/CInterpolatorBase::GetDependencies.md)|获取该内插器的依赖项。  （重写 `CUIAnimationInterpolatorBase::GetDependencies`。）|  
|[CInterpolatorBase::GetDuration](../Topic/CInterpolatorBase::GetDuration.md)|获取该内插器的持续时间。  （重写 `CUIAnimationInterpolatorBase::GetDuration`。）|  
|[CInterpolatorBase::GetFinalValue](../Topic/CInterpolatorBase::GetFinalValue.md)|获取由该内插器产生的最终值。  （重写 `CUIAnimationInterpolatorBase::GetFinalValue`。）|  
|[CInterpolatorBase::InterpolateValue](../Topic/CInterpolatorBase::InterpolateValue.md)|内插该值在特定偏移量\(重写 `CUIAnimationInterpolatorBase::InterpolateValue`。）|  
|[CInterpolatorBase::InterpolateVelocity](../Topic/CInterpolatorBase::InterpolateVelocity.md)|内插速度在特定偏移量\(重写 `CUIAnimationInterpolatorBase::InterpolateVelocity`。）|  
|[CInterpolatorBase::SetCustomInterpolator](../Topic/CInterpolatorBase::SetCustomInterpolator.md)|存储指向将要处理事件的自定义内插器的指针。|  
|[CInterpolatorBase::SetDuration](../Topic/CInterpolatorBase::SetDuration.md)|设置重项的持续时间\(重写 `CUIAnimationInterpolatorBase::SetDuration`。）|  
|[CInterpolatorBase::SetInitialValueAndVelocity](../Topic/CInterpolatorBase::SetInitialValueAndVelocity.md)|设置内插器的初始值和速度。  （重写 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。）|  
  
## 备注  
 此处理程序中创建并传递给 `IUIAnimationTransitionFactory::CreateTransition`，当 `CCustomTransition` 对象创建时，动画的部分初始化过程\(从 `CAnimationController::AnimateGroup`）。  通常不需要直接使用此选件类，它击溃所有事件。`CCustomInterpolator`派生类，指针传递给 `CCustomTransition`构造函数。  
  
## 继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)