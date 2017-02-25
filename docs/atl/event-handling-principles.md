---
title: "Event Handling Principles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "双重接口, event interfaces"
  - "事件处理, advising event sources"
  - "事件处理, dual event interfaces"
  - "事件处理, 实现"
  - "接口, event and event sink"
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Event Handling Principles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有三个步骤共有的所有事件处理。  您需要:  
  
-   实现对象的事件接口。  
  
-   建议事件源您的对象要接收事件。  
  
-   Unadvise事件源，当对象不再需要接收事件。  
  
 您将实现接口的方法取决于其类型。  事件接口可以是vtable，、或调度接口。  将由定义的接口事件源的设计器;将由实现该接口的。  
  
> [!NOTE]
>  虽然在技术上的原因事件接口不能是双的，有多种虚拟设计原因避免使用双绑定。  但是，这种 *事件源的*设计器\/实现所做的决策。  因为您从活动 `sink`的角度工作，您需要允许这种可能性您可能没有任何选择，但实现一个双事件接口。  有关双重接口的更多信息，请参见 [双重接口和ATL](../atl/dual-interfaces-and-atl.md)。  
  
 建议事件源可以分解为三个步骤:  
  
-   查询 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)的源对象。  
  
-   调用通过感兴趣事件接口的IID的 [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476)。  如果成功，则将返回在的 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) 接口的连接点对象。  
  
-   该调用会将事件接收器的 **IUnknown** 的 [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815)。  如果成功，则将返回表示连接的 `DWORD` cookie。  
  
 一旦在接收事件上成功注册了感兴趣，在对象的事件接口的方法根据操作将调用激发的源对象。  当不再需要接收事件时，可以通过cookie回通过 [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608)连接点。  否则会中断连接在源和事件之间。  
  
 在处理事件时，请注意避免循环引用。  
  
## 请参阅  
 [事件处理](../atl/event-handling-and-atl.md)