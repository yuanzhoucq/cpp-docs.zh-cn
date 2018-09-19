---
title: 实现事件处理接口 |Microsoft Docs
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
ms.openlocfilehash: b2241080fda6aa58dc5e70f57c83afec69a57203
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757333"
---
# <a name="implementing-the-event-handling-interface"></a>实现事件处理接口

ATL 可以帮助您完成用于处理事件所需的所有三个元素： 实现事件接口，通知事件源和取消通知事件源。 您需要的精确步骤取决于事件接口和你的应用程序的性能要求的类型。

实现接口使用 ATL 的最常见方法是：

- 直接从自定义接口派生。

- 派生自[IDispatchImpl](../atl/reference/idispatchimpl-class.md)双重接口的类型库中所述。

- 派生自[IDispEventImpl](../atl/reference/idispeventimpl-class.md)对于调度接口的类型库中所述。

- 派生自[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)对于调度接口未描述类型库中或你想要通过不加载在运行时类型信息来提高效率。

如果要实现自定义或双接口，你应建议事件源通过调用[AtlAdvise](reference/connection-point-global-functions.md#atladvise)或[CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)。 您需要跟踪的调用返回自己的 cookie。 调用[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)断开连接。  

如果要实现调度接口使用`IDispEventImpl`或`IDispEventSimpleImpl`，你应建议事件源通过调用[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)。 调用[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)断开连接。

如果使用的`IDispEventImpl`作为复合控件的基类，接收器映射中列出的事件源将建议并 unadvised 使用自动[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。

`IDispEventImpl`和`IDispEventSimpleImpl`类为你管理 cookie。

## <a name="see-also"></a>请参阅

[事件处理](../atl/event-handling-and-atl.md)

