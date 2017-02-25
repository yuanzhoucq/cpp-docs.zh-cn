---
title: "CAnimationStoryboardEventHandler 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationStoryboardEventHandler"
  - "CAnimationStoryboardEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationStoryboardEventHandler 类"
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationStoryboardEventHandler 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现回调，它在演示图板状态更改时或演示图板更新时由动画 API 调用。  
  
## 语法  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](../Topic/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler.md)|构造 `CAnimationStoryboardEventHandler` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationStoryboardEventHandler::CreateInstance](../Topic/CAnimationStoryboardEventHandler::CreateInstance.md)|创建 `CAnimationStoryboardEventHandler` 回调实例。|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](../Topic/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged.md)|处理 `OnStoryboardStatusChanged` 事件，时，会发生演示图板状态更改\(重写 `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`。）|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](../Topic/CAnimationStoryboardEventHandler::OnStoryboardUpdated.md)|处理 `OnStoryboardUpdated` 事件，时，会发生演示图板更新\(重写 `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`。）|  
|[CAnimationStoryboardEventHandler::SetAnimationController](../Topic/CAnimationStoryboardEventHandler::SetAnimationController.md)|存储指向路由事件的动画控制器的指针。|  
  
## 备注  
 在调用 `CAnimationController::EnableStoryboardEventHandler`时，此事件处理程序中创建并传递给 `IUIAnimationStoryboard::SetStoryboardEventHandler` 方法。  
  
## 继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)