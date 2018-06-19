---
title: ATL 事件处理摘要 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a938bd072ea8df30e64cce28fbf0709f08547d28
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356516"
---
# <a name="atl-event-handling-summary"></a>ATL 事件处理摘要
通常情况下，处理 COM 事件是一个相对较简单的过程。 有三个主要步骤：  
  
-   在你的对象上实现事件接口。  
  
-   建议你的对象要接收事件的事件源。  
  
-   当你的对象不再需要要接收事件时，不建议事件源。  
  
## <a name="implementing-the-interface"></a>实现接口  
 有四种主要方法的实现使用 ATL 接口  
  
|派生自|适用于接口类型|需要实现所有方法 *|在运行时需要类型库|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|接口|Vtable|是|否|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|双|是|是|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|调度接口|否|是|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|调度接口|否|否|  
  
 \* 使用 ATL 支持类时，你永远不会要求实现**IUnknown**或`IDispatch`方法手动。  
  
## <a name="advising-and-unadvising-the-event-source"></a>通知和取消通知的事件源  
 有三个方面的通知和取消通知使用 ATL 中的事件源  
  
|建议函数|不建议函数|最适合与一起使用|需要您能够跟踪 cookie|注释|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|  

|[AtlAdvise](reference/connection-point-global-functions.md#atladvise)， [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable 或双重接口 |是 |`AtlAdvise`是全局的 ATL 函数。 `CComPtrBase::Advise` 由[CComPtr](../atl/reference/ccomptr-class.md)和[CComQIPtr](../atl/reference/ccomqiptr-class.md)。 |  

|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)或[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|否 |较少的参数，比`AtlAdvise`原因的基类是更多工作。 |  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|复合控件中的 ActiveX 控件 |否 |`CComCompositeControl::AdviseSinkMap`建议所有条目在事件都接收器映射。 相同的函数取消通知项。 自动调用此方法`CComCompositeControl`类。 |  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|在对话框中的 ActiveX 控件 |否 |`CAxDialogImpl::AdviseSinkMap`建议和取消通知对话框资源中的所有 ActiveX 控件。 这会为你自动完成。 |  
  
## <a name="see-also"></a>请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [支持 IDispEventImpl](../atl/supporting-idispeventimpl.md)

