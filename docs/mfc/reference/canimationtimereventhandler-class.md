---
title: "CAnimationTimerEventHandler 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationTimerEventHandler"
  - "CAnimationTimerEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationTimerEventHandler 类"
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationTimerEventHandler 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现回调，它在计时事件发生时由动画 API 调用。  
  
## 语法  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationTimerEventHandler::CreateInstance](../Topic/CAnimationTimerEventHandler::CreateInstance.md)|创建 `CAnimationTimerEventHandler` 回调实例。|  
|[CAnimationTimerEventHandler::OnPostUpdate](../Topic/CAnimationTimerEventHandler::OnPostUpdate.md)|处理在动画更新完成之后发生的事件。  （重写 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`。）|  
|[CAnimationTimerEventHandler::OnPreUpdate](../Topic/CAnimationTimerEventHandler::OnPreUpdate.md)|处理在动画更新开始之前发生的事件。  （重写 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`。）|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](../Topic/CAnimationTimerEventHandler::OnRenderingTooSlow.md)|处理当动画的呈现帧速率低于最小的理想帧速率时发生的事件。  （重写 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`。）|  
|[CAnimationTimerEventHandler::SetAnimationController](../Topic/CAnimationTimerEventHandler::SetAnimationController.md)|存储指向路由事件的动画控制器的指针。|  
  
## 备注  
 当您调用 CAnimationController::EnableAnimationTimerEventHandler 时，会创建并将此事件处理程序传递给 IUIAnimationTimer::SetTimerEventHandler 方法。  
  
## 继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)