---
title: "Implementing the Event Handling Interface | Microsoft Docs"
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
  - "ATL, 事件处理"
  - "事件处理, ATL"
  - "接口, event and event sink"
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Implementing the Event Handling Interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL帮助您具有用于处理事件所需的全部三个组件的:实现事件接口，建议事件源和unadvising事件源。  您需要采取的准确的步骤确定事件接口的类型和应用程序的性能要求。  
  
 使用ATL实现的接口的最常用方法是:  
  
-   直接从派生的自定义接口。  
  
-   从派生类型中描述的双重接口的 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 库。  
  
-   从派生介绍类型中的调度接口的 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 库。  
  
-   从派生类型上不描述的调度接口的 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 库时，或者当希望通过不加载该类型来提高效率信息在运行时。  
  
 如果实现自定义或双重接口，则应通过调用 [AtlAdvise](../Topic/AtlAdvise.md) 或 [CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)建议事件源。  您将需要跟踪调用返回的cookie。  调用 [AtlUnadvise](../Topic/AtlUnadvise.md) 中断连接。  
  
 使用 `IDispEventImpl` 或 `IDispEventSimpleImpl`，如果实现调度接口，则应通过调用 [IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)建议事件源。  调用 [IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) 中断连接。  
  
 如果使用 `IDispEventImpl` 为复合控件的基类，在接收图中列出的事件源使用 [CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)会自动建议和轻率的。  
  
 `IDispEventImpl` 和 `IDispEventSimpleImpl` 选件类管理您的cookie。  
  
## 请参阅  
 [事件处理](../atl/event-handling-and-atl.md)