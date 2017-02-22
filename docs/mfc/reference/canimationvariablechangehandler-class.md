---
title: "CAnimationVariableChangeHandler 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationVariableChangeHandler"
  - "CAnimationVariableChangeHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariableChangeHandler 类"
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CAnimationVariableChangeHandler 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现回调，它在动画变量值更改时由动画 API 调用。  
  
## 语法  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|构造 `CAnimationVariableChangeHandler` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CAnimationVariableChangeHandler::CreateInstance`|创建 `CAnimationVariableChangeHandler` 对象实例。|  
|[CAnimationVariableChangeHandler::OnValueChanged](../Topic/CAnimationVariableChangeHandler::OnValueChanged.md)|在动画变量的值更改时调用。  （重写 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。）|  
|[CAnimationVariableChangeHandler::SetAnimationController](../Topic/CAnimationVariableChangeHandler::SetAnimationController.md)|存储指向路由事件的动画控制器的指针。|  
  
## 备注  
 此事件处理程序中创建并传递给 `IUIAnimationVariable::SetVariableChangeHandler` 方法，那么，当您调用\(使动画对象封装的所有动画变量的此事件\)的 `CAnimationVariable::EnableValueChangedEvent` 或 `CAnimationBaseObject::EnableValueChangedEvent` 时。  
  
## 继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)