---
title: "CAnimationVariableIntegerChangeHandler 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationVariableIntegerChangeHandler"
  - "CAnimationVariableIntegerChangeHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariableIntegerChangeHandler 类"
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationVariableIntegerChangeHandler 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现回调，它在动画变量值更改时由动画 API 调用。  
  
## 语法  
  
```  
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](../Topic/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler.md)|构造 `CAnimationVariableIntegerChangeHandler` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationVariableIntegerChangeHandler::CreateInstance](../Topic/CAnimationVariableIntegerChangeHandler::CreateInstance.md)|创建 `CAnimationVariableIntegerChangeHandler` 回调实例。|  
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](../Topic/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged.md)|在动画变量的值更改时调用。  （重写 `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`。）|  
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](../Topic/CAnimationVariableIntegerChangeHandler::SetAnimationController.md)|存储指向路由事件的动画控制器的指针。|  
  
## 备注  
 当您调用 CAnimationVariable::EnableIntegerValueChangedEvent 或 CAnimationBaseObject::EnableIntegerValueChangedEvent（这将使此事件用于封装在动画对象中的所有动画变量）时，创建并将此事件处理程序传递给 IUIAnimationVariable::SetVariableIntegerChangeHandler 方法。  
  
## 继承层次结构  
 [MFC 类](../../mfc/reference/mfc-classes.md)  
  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableIntegerChangeHandlerBase`  
  
 `CAnimationVariableIntegerChangeHandler`  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)