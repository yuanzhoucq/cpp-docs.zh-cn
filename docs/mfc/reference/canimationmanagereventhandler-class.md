---
title: "CAnimationManagerEventHandler 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationManagerEventHandler"
  - "CAnimationManagerEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationManagerEventHandler 类"
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationManagerEventHandler 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现回调，它在动画管理器状态更改时由动画 API 调用。  
  
## 语法  
  
```  
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](../Topic/CAnimationManagerEventHandler::CAnimationManagerEventHandler.md)|构造 `CAnimationManagerEventHandler` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationManagerEventHandler::CreateInstance](../Topic/CAnimationManagerEventHandler::CreateInstance.md)|创建 `CAnimationManagerEventHandler` 对象实例。|  
|[CAnimationManagerEventHandler::OnManagerStatusChanged](../Topic/CAnimationManagerEventHandler::OnManagerStatusChanged.md)|当动画管理器的状态更改后调用。  （重写 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。）|  
|[CAnimationManagerEventHandler::SetAnimationController](../Topic/CAnimationManagerEventHandler::SetAnimationController.md)|存储指向路由事件的动画控制器的指针。|  
  
## 备注  
 当您调用 CAnimationController::EnableAnimationManagerEvent 时，会创建并将此事件处理程序传递给 IUIAnimationManager::SetManagerEventHandler 方法。  
  
## 继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)