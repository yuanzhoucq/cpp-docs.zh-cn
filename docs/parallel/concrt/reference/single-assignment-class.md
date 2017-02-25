---
title: "single_assignment 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::single_assignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single_assignment 类"
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# single_assignment 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`single_assignment` 消息块是一个多目标、多源、有序的 `propagator_block`，能够存储单个、只写一次的 `message`。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class single_assignment : public propagator_block<multi_link_registry<ITarget<_Type>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### 参数  
 `_Type`  
 缓冲区存储的和传播的消息的负载类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[single\_assignment::single\_assignment 构造函数](../Topic/single_assignment::single_assignment%20Constructor.md)|已重载。  构造 `single_assignment` 消息块。|  
|[single\_assignment::~single\_assignment 析构函数](../Topic/single_assignment::~single_assignment%20Destructor.md)|销毁 `single_assignment` 消息块。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[single\_assignment::has\_value 方法](../Topic/single_assignment::has_value%20Method.md)|检查该 `single_assignment` 消息该块是否已经使用一个值初始化。|  
|[single\_assignment::value 方法](../Topic/single_assignment::value%20Method.md)|获取对当前存储在 `single_assignment` 消息块中消息的当前负载的引用。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[single\_assignment::accept\_message 方法](../Topic/single_assignment::accept_message%20Method.md)|接受由此 `single_assignment` 消息块提供的消息，将消息副本返还给调用方。|  
|[single\_assignment::consume\_message 方法](../Topic/single_assignment::consume_message%20Method.md)|使用先前由 `single_assignment` 提供并由目标保留的消息，将消息副本返还给调用方。|  
|[single\_assignment::link\_target\_notification 方法](../Topic/single_assignment::link_target_notification%20Method.md)|通知新的目标已链接至此 `single_assignment` 消息块的回调。|  
|[single\_assignment::propagate\_message 方法](../Topic/single_assignment::propagate_message%20Method.md)|将 `ISource` 块中的消息异步传递到此 `single_assignment` 消息块中。  在由源块调用时，其由 `propagate` 方法调用。|  
|[single\_assignment::propagate\_to\_any\_targets 方法](../Topic/single_assignment::propagate_to_any_targets%20Method.md)|将 `message``_PMessage` 放置在此 `single_assignment` 消息块中，并将它提供给所有链接目标。|  
|[single\_assignment::release\_message 方法](../Topic/single_assignment::release_message%20Method.md)|释放以前的消息保留。（覆盖 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)。）|  
|[single\_assignment::reserve\_message 方法](../Topic/single_assignment::reserve_message%20Method.md)|保留此 `single_assignment` 消息块之前提供的消息。（覆盖 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)。）|  
|[single\_assignment::resume\_propagation 方法](../Topic/single_assignment::resume_propagation%20Method.md)|释放保留后继续传播。（覆盖 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)。）|  
|[single\_assignment::send\_message 方法](../Topic/single_assignment::send_message%20Method.md)|将消息从 `ISource` 块同步传递到此 `single_assignment` 消息块中。  在由源块调用时，其由 `send` 方法调用。|  
  
## 备注  
 `single_assignment` 消息块将其消息的副本传播到每个目标。  
  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `single_assignment`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [overwrite\_buffer 类](../../../parallel/concrt/reference/overwrite-buffer-class.md)   
 [unbounded\_buffer 类](../Topic/unbounded_buffer%20Class.md)