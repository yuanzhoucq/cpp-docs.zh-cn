---
title: "ATL Event Handling Summary | Microsoft Docs"
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
  - "事件处理, 实现"
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ATL Event Handling Summary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，处理COM事件是一个相对简单的过程。  有三个主要步骤:  
  
-   实现对象的事件接口。  
  
-   建议事件源您的对象要接收事件。  
  
-   Unadvise事件源，当对象不再需要接收事件。  
  
## 实现接口  
 使用ATL实现接口，有四种主要方式。  
  
|从  派生|适用于接口类型|需要实现所有methods\*|需要类型库在运行时|  
|-----------|-------------|---------------------|---------------|  
|接口|Vtable|是|否|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|双重|是|是|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|调度接口|否|是|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|调度接口|否|否|  
  
 \*在使用ATL时支持选件类，不需要手动执行 **IUnknown** 或 `IDispatch` 方法。  
  
## 建议和Unadvising事件源  
 使用ATL，建议和unadvising事件源三种主要方式。  
  
|建议功能|Unadvise功能|适用于|要求您记录cookie?|注释|  
|----------|----------------|---------|------------------|--------|  
|[AtlAdvise](../Topic/AtlAdvise.md)，[CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)|[AtlUnadvise](../Topic/AtlUnadvise.md)|Vtable或双重接口|是|`AtlAdvise` 是全局ATL功能。  [CComPtr](../atl/reference/ccomptr-class.md) 和 [CComQIPtr](../atl/reference/ccomqiptr-class.md)使用`CComPtrBase::Advise`。|  
|[IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)|[IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) 或 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|否|较少形参比 `AtlAdvise`，因为基类完成更多工作。|  
|[CComCompositeControl::AdviseSinkMap \(TRUE\)](../Topic/CComCompositeControl::AdviseSinkMap.md)|[CComCompositeControl::AdviseSinkMap \(FALSE\)](../Topic/CComCompositeControl::AdviseSinkMap.md)|在复合控件的ActiveX控件|否|`CComCompositeControl::AdviseSinkMap` 建议在事件接收器映射的所有项。  功能相同unadvises项。  此方法由 `CComCompositeControl` 选件类自动调用。|  
|[CAxDialogImpl::AdviseSinkMap \(TRUE\)](../Topic/CAxDialogImpl::AdviseSinkMap.md)|[CAxDialogImpl::AdviseSinkMap \(FALSE\)](../Topic/CAxDialogImpl::AdviseSinkMap.md)|在对话框的ActiveX控件|否|`CAxDialogImpl::AdviseSinkMap` 建议和unadvises在对话框资源的所有ActiveX控件。  这对于自动执行。|  
  
## 请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [Supporting IDispEventImpl](../atl/supporting-idispeventimpl.md)