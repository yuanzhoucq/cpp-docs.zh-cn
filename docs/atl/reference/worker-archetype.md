---
title: "Worker Archetype | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Worker archetype"
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Worker Archetype
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符合 *辅助* 原型的选件类提供代码对线程池队列的处理工作项。  
  
 **实现**  
  
 若要实现选件类与此原型，选件类必须提供以下功能:  
  
|方法|说明|  
|--------|--------|  
|[初始化](../Topic/WorkerArchetype::Initialize.md)|对所有请求之前初始化辅助对象传递给 [执行](../Topic/WorkerArchetype::Execute.md)。|  
|[执行](../Topic/WorkerArchetype::Execute.md)|调用处理工作项。|  
|[终止](../Topic/WorkerArchetype::Terminate.md)|调用uninitialize辅助对象，在所有请求传递给 [执行](../Topic/WorkerArchetype::Execute.md)之后。|  
  
|Typedef|说明|  
|-------------|--------|  
|[RequestType](../Topic/WorkerArchetype::RequestType.md)|可由辅助选件类处理工作项类型的typedef。|  
  
 典型的 *辅助* 选件类如下所示:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/CPP/worker-archetype_1.cpp)]  
  
 **现有实现**  
  
 这些选件类符合此原型:  
  
|类|说明|  
|-------|--------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|接收来自线程池的请求并传递到对每个请求创建和销毁的辅助对象。|  
  
 **使用**  
  
 这些模板参数希望选件类符合此原型:  
  
|参数名|使用者|  
|---------|---------|  
|*辅助*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*辅助*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [Archetypes](../../atl/reference/atl-archetypes.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)