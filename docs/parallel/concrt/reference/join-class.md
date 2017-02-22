---
title: "join 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::join"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "join 类"
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# join 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`join` 消息块是一个单目标、多源、有序的 `propagator_block`，可以合并来自其每个源的类型为 `_Type` 的消息。  
  
## 语法  
  
```  
template<  
   class _Type,  
   join_type _Jtype = non_greedy  
>  
class join : public propagator_block<single_link_registry<ITarget<std::vector<_Type>>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### 参数  
 `_Type`  
 块联接的和传播的消息的负载类型。  
  
 `_Jtype`  
 `join` 块的种类为 `greedy` 或 `non_greedy`  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[join::join 构造函数](../Topic/join::join%20Constructor.md)|已重载。  构造 `join` 消息块。|  
|[join::~join 析构函数](../Topic/join::~join%20Destructor.md)|销毁 `join` 块。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[join::accept\_message 方法](../Topic/join::accept_message%20Method.md)|接受由此 `join` 消息块提供的消息，将所有权转移给调用方。|  
|[join::consume\_message 方法](../Topic/join::consume_message%20Method.md)|使用先前由 `join` 消息块提供并由目标保留的消息，将所有权转移给调用方。|  
|[join::link\_target\_notification 方法](../Topic/join::link_target_notification%20Method.md)|通知新的目标已链接至此 `join` 消息块的回调。|  
|[join::propagate\_message 方法](../Topic/join::propagate_message%20Method.md)|将 `ISource` 块中的消息异步传递到此 `join` 消息块中。  在由源块调用时，其由 `propagate` 方法调用。|  
|[join::propagate\_to\_any\_targets 方法](../Topic/join::propagate_to_any_targets%20Method.md)|在每个源均传播了消息时，构造包含来自每个源的输入消息的输出消息。  将此输出消息发送到其每个目标。|  
|[join::release\_message 方法](../Topic/join::release_message%20Method.md)|释放以前的消息保留。（覆盖 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)。）|  
|[join::reserve\_message 方法](../Topic/join::reserve_message%20Method.md)|保留此 `join` 消息块之前提供的消息。（覆盖 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)。）|  
|[join::resume\_propagation 方法](../Topic/join::resume_propagation%20Method.md)|释放保留后继续传播。（覆盖 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)。）|  
  
## 备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `join`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [choice 类](../../../parallel/concrt/reference/choice-class.md)   
 [multitype\_join 类](../../../parallel/concrt/reference/multitype-join-class.md)   
 [join\_type 枚举](../Topic/join_type%20Enumeration.md)