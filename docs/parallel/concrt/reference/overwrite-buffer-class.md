---
title: "overwrite_buffer 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::overwrite_buffer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "overwrite_buffer 类"
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# overwrite_buffer 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`overwrite_buffer` 消息块是一个多目标、多源、有序的 `propagator_block`，一次能够存储一条消息。  新消息覆盖之前保存的消息。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<_Type>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### 参数  
 `_Type`  
 缓冲区存储的和传播的消息的负载类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[overwrite\_buffer::overwrite\_buffer 构造函数](../Topic/overwrite_buffer::overwrite_buffer%20Constructor.md)|已重载。  构造 `overwrite_buffer` 消息块。|  
|[overwrite\_buffer::~overwrite\_buffer 析构函数](../Topic/overwrite_buffer::~overwrite_buffer%20Destructor.md)|销毁 `overwrite_buffer` 消息块。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[overwrite\_buffer::has\_value 方法](../Topic/overwrite_buffer::has_value%20Method.md)|检查此 `overwrite_buffer` 消息块是否已具有一个值。|  
|[overwrite\_buffer::value 方法](../Topic/overwrite_buffer::value%20Method.md)|获取对当前存储在 `overwrite_buffer` 消息块中消息的当前负载的引用。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[overwrite\_buffer::accept\_message 方法](../Topic/overwrite_buffer::accept_message%20Method.md)|接受由此 `overwrite_buffer` 消息块提供的消息，将消息副本返还给调用方。|  
|[overwrite\_buffer::consume\_message 方法](../Topic/overwrite_buffer::consume_message%20Method.md)|使用先前由 `overwrite_buffer` 消息块提供并由目标保留的消息，将消息副本返还给调用方。|  
|[overwrite\_buffer::link\_target\_notification 方法](../Topic/overwrite_buffer::link_target_notification%20Method.md)|通知新的目标已链接至此 `overwrite_buffer` 消息块的回调。|  
|[overwrite\_buffer::propagate\_message 方法](../Topic/overwrite_buffer::propagate_message%20Method.md)|将 `ISource` 块中的消息异步传递到此 `overwrite_buffer` 消息块中。  在由源块调用时，其由 `propagate` 方法调用。|  
|[overwrite\_buffer::propagate\_to\_any\_targets 方法](../Topic/overwrite_buffer::propagate_to_any_targets%20Method.md)|将 `message``_PMessage` 放置在此 `overwrite_buffer` 消息块中，并将它提供给所有链接目标。|  
|[overwrite\_buffer::release\_message 方法](../Topic/overwrite_buffer::release_message%20Method.md)|释放以前的消息保留。（覆盖 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)。）|  
|[overwrite\_buffer::reserve\_message 方法](../Topic/overwrite_buffer::reserve_message%20Method.md)|保留此 `overwrite_buffer` 消息块之前提供的消息。（覆盖 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)。）|  
|[overwrite\_buffer::resume\_propagation 方法](../Topic/overwrite_buffer::resume_propagation%20Method.md)|释放保留后继续传播。（覆盖 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)。）|  
|[overwrite\_buffer::send\_message 方法](../Topic/overwrite_buffer::send_message%20Method.md)|将消息从 `ISource` 块同步传递到此 `overwrite_buffer` 消息块中。  在由源块调用时，其由 `send` 方法调用。|  
|[overwrite\_buffer::supports\_anonymous\_source 方法](../Topic/overwrite_buffer::supports_anonymous_source%20Method.md)|重写 `supports_anonymous_source` 方法表示此块可以接受未链接的源为其提供的消息。重写 \( [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md)。\)|  
  
## 备注  
 `overwrite_buffer` 消息块将其存储的消息的副本传播到每个目标。  
  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [unbounded\_buffer 类](../Topic/unbounded_buffer%20Class.md)   
 [single\_assignment 类](../../../parallel/concrt/reference/single-assignment-class.md)