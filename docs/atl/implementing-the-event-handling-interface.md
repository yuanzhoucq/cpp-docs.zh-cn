---
title: 实现的事件处理接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea37aa4c84cb0824d11f0081e38d9e8157b77ed1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-the-event-handling-interface"></a>实现的事件处理接口
ATL 可帮助你具有所需的处理事件的所有三个元素： 实现事件接口、 通知事件源和取消通知事件源。 你将需要采取的精确步骤取决于事件接口和你的应用程序的性能要求的类型。  
  
 实现接口使用 ATL 的最常见方法是：  
  
-   直接从自定义接口派生。  
  
-   派生自[IDispatchImpl](../atl/reference/idispatchimpl-class.md)双重接口的类型库中所述。  
  
-   派生自[IDispEventImpl](../atl/reference/idispeventimpl-class.md)对于调度接口的类型库中所述。  
  
-   派生自[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)对于调度接口未描述类型库中或者在你想要通过不在加载运行时类型信息来提高效率。  
  

 如果你要实现自定义或双重接口，你应通过调用告知事件源[AtlAdvise](reference/connection-point-global-functions.md#atladvise)或[CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)。 你将需要跟踪的调用所返回您自己的 cookie。 调用[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)以断开的连接。  

  
 如果你要实现调度接口使用`IDispEventImpl`或`IDispEventSimpleImpl`，你应通过调用建议事件源[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)。 调用[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)以断开的连接。  
  
 如果你使用`IDispEventImpl`作为复合控件的基类，接收器图中列出的事件源将建议和 unadvised 使用自动[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。  
  
 `IDispEventImpl`和`IDispEventSimpleImpl`类为你管理 cookie。  
  
## <a name="see-also"></a>请参阅  
 [事件处理](../atl/event-handling-and-atl.md)

