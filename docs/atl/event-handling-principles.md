---
title: "事件处理原则 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c37544f7b9083bbfa890961ef40e0c9f26aecc2c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="event-handling-principles"></a>事件处理原则
有三个步骤普遍适用于所有事件处理。 你将需要：  
  
-   在你的对象上实现事件接口。  
  
-   建议你的对象要接收事件的事件源。  
  
-   当你的对象不再需要要接收事件时，不建议事件源。  
  
 你将实施事件接口的方法将取决于其类型。 Vtable、 双或调度接口，可以是事件接口。 这取决于事件源的设计器定义接口;它是最多可以实现该接口来决定。  
  
> [!NOTE]
>  尽管不有任何事件接口不能是双重的技术原因，不有多种良好的设计原因，以避免使用双接口。 但是，这是由设计器/事件的实施者决定*源*。 由于你正在从该事件的角度`sink`，你需要允许是否可能会出现，你可能没有选择任何但要实现双事件接口。 双重接口的详细信息，请参阅[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)。  
  
 通知事件源可以分为三个步骤：  
  
-   查询的源对象[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)。  
  
-   调用[IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476)传递事件接口的 IID 感兴趣。 如果成功，这将返回[IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)连接点对象上的接口。  
  
-   调用[IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815)传递**IUnknown**的事件接收器。 如果成功，这将返回`DWORD`表示连接的 cookie。  
  
 一旦你已成功注册您有兴趣接收事件，将根据源对象激发的事件调用对象的事件接口方法。 当你不再需要要接收事件时，可以将 cookie 传递回连接点通过[IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608)。 这会使源和接收器之间的连接。  
  
 请注意避免引用时处理事件周期。  
  
## <a name="see-also"></a>另请参阅  
 [事件处理](../atl/event-handling-and-atl.md)

